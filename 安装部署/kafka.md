[TOC]

# wiki
(wiki)(https://kafka.apache.org/)

# download
(download)[https://kafka.apache.org/downloads]

wget https://dlcdn.apache.org/kafka/3.9.0/kafka-3.9.0-src.tgz

tar -zxvf kafka-3.9.0-src.tgz
mv kafka-3.9.0-src /opt/kafka

# config
vim server.properties
```
broker.id=0
num.network.threads=3
num.io.threads=8
socket.send.buffer.bytes=102400
socket.receive.buffer.bytes=102400
socket.request.max.bytes=104857600
log.dirs=/tmp/kafka-logs
num.partitions=1
num.recovery.threads.per.data.dir=1
offsets.topic.replication.factor=1
transaction.state.log.replication.factor=1
transaction.state.log.min.isr=1
log.retention.hours=168
log.retention.check.interval.ms=300000
zookeeper.connect=zookeeper:2181
zookeeper.connection.timeout.ms=18000
group.initial.rebalance.delay.ms=0
listeners=PLAINTEXT://kafka:9092,SASL_PLAINTEXT://kafka:9091
advertised.listeners=PLAINTEXT://kafka:9092,SASL_PLAINTEXT://kafka:9091
security.inter.broker.protocol=SASL_PLAINTEXT
sasl.mechanism.inter.broker.protocol=GSSAPI
sasl.enabled.mechanisms=GSSAPI
sasl.kerberos.service.name=kafka
authorizer.class.name=kafka.security.authorizer.AclAuthorizer
allow.everyone.if.no.acl.found=false
super.users=User:kafka
```

vim kafka.jaas
```
KafkaServer {
  com.sun.security.auth.module.Krb5LoginModule required
  useKeyTab=true
  keyTab="/tmp/kafka.keytab"
  storeKey=true
  useTicketCache=false
  principal="kafka/kafka@EXAMPLE.COM";
};
Client {
  com.sun.security.auth.module.Krb5LoginModule required
  useKeyTab=true
  keyTab="/tmp/kafka.keytab"
  storeKey=true
  useTicketCache=false
  serviceName="kafka"
  principal="kafka/kafkaEXAMPLE.COM";
};
KafkaClient {
  com.sun.security.auth.module.Krb5LoginModule required
  useKeyTab=true
  keyTab="/tmp/kafka.keytab"
  storeKey=true
  useTicketCache=false
  serviceName="kafka"
  principal="kafka/kafka@EXAMPLE.COM";
};
```

vim bin/kafka-server-start.sh
```
export KAFKA_OPTS="-Djava.security.auth.login.config=/opt/kafka/config/kafka_server.jaas -Dsun.security.krb5.debug=true -Djava.security.krb5.conf=/etc/krb5.conf -Xmx2048M -Xms2048M"
```
