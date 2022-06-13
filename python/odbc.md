sudo pacman -S unixodbc freetds

vim /etc/freetds/freetds.conf
[Sybase]
        host = 127.0.0.1
        port = 5000
        tds version = 5.0
        client charset = UTF-8

vim /etc/odbcinst.ini
[FreeTDS]
Description             = FreeTDS unixODBC Driver
Driver          = /usr/lib64/libtdsodbc.so.0
Setup           = /usr/lib64/libtdsodbc.so.0
UsageCount              = 1