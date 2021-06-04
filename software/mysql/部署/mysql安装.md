[TOC]

# 二进制安装
## step-1:安装mysql
```
>sudo pacman -S mysql
```
## step-2:初始化mysql
```
>sudo mysqld --initialize --user=mysql --basedir=/usr --datadir=/var/lib/mysql
2020-02-21T14:31:50.620174Z 0 [System] [MY-013169] [Server] /usr/local/mysql/bin/mysqld (mysqld 8.0.19) initializing of server in progress as process 23491
2020-02-21T14:31:50.620201Z 0 [ERROR] [MY-010338] [Server] Can't find error-message file '/usr/share/errmsg.sys'. Check error-message file location and 'lc-messages-dir' configuration directive.
2020-02-21T14:31:52.884108Z 5 [Note] [MY-010454] [Server] A temporary password is generated for root@localhost: FlXc2mRzj_%q

2020-02-21T14:36:12.322794Z 0 [System] [MY-013169] [Server] /usr/local/mysql/bin/mysqld (mysqld 8.0.19) initializing of server in progress as process 24225
2020-02-21T14:36:14.406953Z 5 [Note] [MY-010454] [Server] A temporary password is generated for root@localhost: JClaW/Wuf24g
```
## step-3:启动mysqld.server
```
>systemctl start mysqld
```
## step-4:修改密码
```
>mysql -uroot -p
>alter user 'root'@'localhost' identified by '123456';
>alter user user() identified by '123456';
```

# 源码安装
## step-1:下载mysql源码
```
>wget ... or kget ...
```

## step-2:解压xd格式
```
>xd -d mysql-8.0.19-linux-glibc2.12-x86_64.tar.xd
```

## step-3:解压tar格式
```
>tar -vf mysql-8.0.19-linux-glibc2.12-x86_64.tar
```

## step-4:移动到/usr/local
```
>mv mysql /usr/local/mysql
```

## step-5:创建mysql用户
```
>adduser mysql
>useradd mysql
```

## step-6:创建文件夹
```
>sudo mkdir data sql_log undo
```

## step-7:赋予权限
```
>sudo chown mysql:mysql -R data/ sql_log/ undo/
```

## step-8:配置命令
```
>sudo nvim /etc/profile
export PATH=$PATH:/usr/local/mysql/bin
source /etc/profile
```

## step-9:拷贝my.cnf模板到/etc/my.cnf
```
[client]
port            = 3306
socket          = /usr/local/mysql/data/mysql.sock
[mysqld]
# Skip #
skip_name_resolve              = 1
skip_external_locking          = 1 
skip_symbolic_links     = 1
# GENERAL #
user = mysql
default_storage_engine = InnoDB
character-set-server = utf8
socket  = /usr/local/mysql/data/mysql.sock
pid_file = /usr/local/mysql/data/mysqld.pid
basedir = /usr/local/mysql
port = 3306
bind-address = 0.0.0.0
explicit_defaults_for_timestamp = off
sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES
#read_only=on
# MyISAM #
key_buffer_size                = 32M
#myisam_recover                 = FORCE,BACKUP

# undo log #
innodb_undo_directory = /usr/local/mysql/undo
innodb_undo_tablespaces = 8

# SAFETY #
max_allowed_packet             = 100M
max_connect_errors             = 1000000
sysdate_is_now                 = 1
#innodb = FORCE
#innodb_strict_mode = 1
secure-file-priv='/tmp'
default_authentication_plugin='mysql_native_password'
# Replice #
 server-id = 1001
 relay_log = mysqld-relay-bin
 gtid_mode = on
 enforce-gtid-consistency
 log-slave-updates = on
 master_info_repository =TABLE
 relay_log_info_repository =TABLE


# DATA STORAGE #
 datadir = /usr/local/mysql/data/
 tmpdir = /tmp
 
# BINARY LOGGING #
 log_bin = /usr/local/mysql/sql_log/mysql-bin
 max_binlog_size = 1000M
 binlog_format = row
 binlog_expire_logs_seconds=86400
# sync_binlog = 1

 # CACHES AND LIMITS #
 tmp_table_size                 = 32M
 max_heap_table_size            = 32M
 max_connections                = 4000
 thread_cache_size              = 2048
 open_files_limit               = 65535
 table_definition_cache         = 4096
 table_open_cache               = 4096
 sort_buffer_size               = 2M
 read_buffer_size               = 2M
 read_rnd_buffer_size           = 2M
# thread_concurrency             = 24
 join_buffer_size = 1M
# table_cache = 32768
 thread_stack = 512k
 max_length_for_sort_data = 16k


 # INNODB #
 innodb_flush_method            = O_DIRECT
 innodb_log_buffer_size = 16M
 innodb_flush_log_at_trx_commit = 2
 innodb_file_per_table          = 1
 innodb_buffer_pool_size        = 256M
 #innodb_buffer_pool_instances = 8
 innodb_stats_on_metadata = off
 innodb_open_files = 8192
 innodb_read_io_threads = 16
 innodb_write_io_threads = 16
 innodb_io_capacity = 20000
 innodb_thread_concurrency = 0
 innodb_lock_wait_timeout = 60
 innodb_old_blocks_time=1000
 innodb_use_native_aio = 1
 innodb_purge_threads=1
 innodb_change_buffering=all
 innodb_log_file_size = 64M
 innodb_log_files_in_group = 2
 innodb_data_file_path  = ibdata1:256M:autoextend
 
 innodb_rollback_on_timeout=on
 # LOGGING #
 log_error                      = /usr/local/mysql/sql_log/mysql-error.log
 # log_queries_not_using_indexes  = 1
 # slow_query_log                 = 1
  slow_query_log_file            = /usr/local/mysql/sql_log/slowlog.log

 # TimeOut #
 #interactive_timeout = 30
 #wait_timeout        = 30
 #net_read_timeout = 60

[mysqldump]
quick
max_allowed_packet = 100M

[mysql]
no-auto-rehash
# Remove the next comment character if you are not familiar with SQL
#safe-updates

[myisamchk]
key_buffer_size = 256M
sort_buffer_size = 256M
read_buffer = 2M
write_buffer = 2M

[mysqlhotcopy]
interactive-timeout
```

## step-10:初始化mysql
```
>mysqld --initialize --user=mysql --basedir=/usr/local/mysql --datadir=/usr/local/mysql/data
```

## step-11:配置服务
```
>cp /support-files/mysql.server /etc/init.d/mysqld
```

## step-12:启动服务
```
>/etc/init.d/mysqld start
```

## step-13:修改密码

