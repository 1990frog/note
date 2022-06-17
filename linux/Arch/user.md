[TOC]

# root密码
理论上有了sudo，我们就不必再用root账号了。但这并不表示绝对安全，因为TTY模式下还能输入root账号名来登录root账号，而且默认是没有密码的！
更重要的是，访客也可以通过ssh等来直接登录！
```
> sudo -i
> passwd
```

# 授予sudo权限
使用visudo工具来编辑sudo的配置文件，所有能使用sudo来执行命令的用户，都应当是“wheel”这个用户组的成员。因此，我们要在wheel组的用户使用sudo
```
> visudo
// 取消[%whell All = (All) All]的注释
```
在Linux中wheel组就类似于一个管理员的组。
通常在LUNIX下，即使我们有系统管理员root的权限，也不推荐用root用户登录。一般情况下用普通用户登录就可以了，在需要root权限执行一些操作时，再su登录成为root用户。但是，任何人只要知道了root的密码，就都可以通过su命令来登录为root用户--这无疑为系统带来了安全隐患。所以，将普通用户加入到wheel组，被加入的这个普通用户就成了管理员组内的用户，但如果不对一些相关的配置文件进行配置，这个管理员组内的用户与普通用户也没什么区别--就像警察下班后，没有带枪、穿这便衣和普通人（用户）一样，虽然他的的确确是警察。

# 创建用户
创建一个新用户，以后登录就用它，配合sudo，取代默认的root用户，提高安全性。
使用useradd来创建用户：
useradd -G wheel -m 用户名，其中-m参数代表自动创建用户的家目标。
passwd 用户名
```
> useradd -G wheel -m [username]
> passwd [username]
> ls /home
```