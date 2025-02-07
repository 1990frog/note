

```
usage: ssh [-1246AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-E log_file] [-e escape_char]
           [-F configfile] [-I pkcs11] [-i identity_file]
           [-J [user@]host[:port]] [-L address] [-l login_name] [-m mac_spec]
           [-O ctl_cmd] [-o option] [-p port] [-Q query_option] [-R address]
           [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]
```

# Permission denied (publickey,gssapi-keyex,gssapi-with-mic)
```
> vim /etc/ssh/sshd_config
PermitRootLogin yes
PubkeyAuthentication no
PasswordAuthentication yes
```

PermitRootLogin 值为yes，表示允许远程连接。
PubkeyAuthentication 值为no，表示关闭公钥验证。
PasswordAuthentication 值为yes，表示开启密码验证。

sudo service sshd restart
