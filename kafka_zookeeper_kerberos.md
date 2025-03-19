# 部署 kerberos

# 安装
arch 
```
> pacman -S krb5
> systemctl enable krb5-kdc
```

## 配置文件
/etc/krb5.conf
```
[libdefaults]
    default_realm = EXAMPLE.COM

[realms]
    EXAMPLE.COM = {
        admin_server = kerberos.example.com
        kdc = kerberos.example.com
        default_principal_flags = +preauth
    }

[domain_realm]
    example.com  = EXAMPLE.COM
    .example.com = EXAMPLE.COM

[logging]
    kdc          = SYSLOG:NOTICE
    admin_server = SYSLOG:NOTICE
    default      = SYSLOG:NOTICE
```

## 命令
### 进入管理页面
kadmin.local

kdb5_util create -s -r EXAMPLE.COM

kadmin.local -q "ktadd -k /tmp/zookeeper.keytab zookeeper/localhost@EXAMPLE.COM"

kadmin.local -q "add_principal -randkey zookeeper/localhost@EXAMPLE.COM"

klist

kinit -kt /tmp/xxx.keytab xxx/xxx@EXAMPLE.COM 


# zookeeper
wget https://dlcdn.apache.org/zookeeper/zookeeper-3.7.2/apache-zookeeper-3.7.2-bin.tar.gz

tar -zxf apache-zookeeper-3.7.2-bin.tar.gz

cp zoo_sample.cfg zoo.cfg

bin/zkServer.sh start

# kafka
wget https://archive.apache.org/dist/kafka/2.0.1/kafka_2.11-2.0.1.tgz
tar -zxf kafka_2.11-2.0.1.tgz

vim config/server.properties
```
broker.id=0
listeners=PLAINTEXT://kafka:9092,SASL_PLAINTEXT://kafka:9091
advertised.listeners=PLAINTEXT://kafka:9092,SASL_PLAINTEXT://kafka:9091

security.inter.broker.protocol=SASL_PLAINTEXT
sasl.mechanism.inter.broker.protocol=GSSAPI
sasl.enabled.mechanisms=GSSAPI
sasl.kerberos.service.name=kafka
zookeeper.connect=localhost:2181/kafka
```

vim config/kafka.jaas
```
KafkaServer {
com.sun.security.auth.module.Krb5LoginModule required
useKeyTab=true
storeKey=true
keyTab="/tmp/kafka.keytab"
principal="kafka/kafka@EXAMPLE.COM";
};
KafkaClient {
com.sun.security.auth.module.Krb5LoginModule required
useKeyTab=true
storeKey=truekeyTab="/etc/security/keytabs/kafka.keytab"
principal="kafka/kafka@EXAMPLE.COM";
};
```

mkdir -m 755 -p /etc/kafka/conf
ln -s kafka.jaas /etc/kafka/conf/kafka.jaas

vim bin/kafka-server-start.sh
```
export KAFKA_OPTS="-Djava.security.krb5.conf=/etc/krb5.conf -Djavax.security.auth.useSubjectCredsOnly=false -Djava.security.auth.login.config=/etc/kafka/conf/kafka.jaas"
export KAFKA_JMX_OPTS="-Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false -Djava.rmi.server.hostname=kafka -Dcom.sun.management.jmxremote.rmi.port=8096 -Dcom.sun.management.jmxremote.local.only=false -Dcom.sun.management.jmxremote.port=8096"
```