[TOC]

# 安装
arch 
pacman -S krb5

centos
yum install krb6-server krb5-libs krb5-workstation

# 配置文件
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
    kdc = FILE:/var/log/krb5kdc.log
    admin_server = FILE:/var/log/kadmin.log
    default = FILE:/var/log/krb5lib.log
```

# 命令
创建数据库
kdb5_util create -r EXAMPLE.COM -s

新增用户
kadmin.local -q "addprinc admin/admin"

导出证书
kadmin.local -q "ktadd -k ./xxx.keytab xxx/xxx@EXAMPLE.COM"

验证证书
kinit -kt xxx.keytab xxx/xxx@EXAMPLE.COM
