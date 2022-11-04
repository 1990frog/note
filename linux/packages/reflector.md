<!-- TOC -->

- [安装reflector](#%E5%AE%89%E8%A3%85reflector)
- [用法](#%E7%94%A8%E6%B3%95)
    - [根据下载速度进行排序，并筛选出前 5 个最近同步的镜像，最后将结果覆写到 /etc/pacman.d/mirrorlist 文件内](#%E6%A0%B9%E6%8D%AE%E4%B8%8B%E8%BD%BD%E9%80%9F%E5%BA%A6%E8%BF%9B%E8%A1%8C%E6%8E%92%E5%BA%8F%E5%B9%B6%E7%AD%9B%E9%80%89%E5%87%BA%E5%89%8D-5-%E4%B8%AA%E6%9C%80%E8%BF%91%E5%90%8C%E6%AD%A5%E7%9A%84%E9%95%9C%E5%83%8F%E6%9C%80%E5%90%8E%E5%B0%86%E7%BB%93%E6%9E%9C%E8%A6%86%E5%86%99%E5%88%B0-etcpacmandmirrorlist-%E6%96%87%E4%BB%B6%E5%86%85)
    - [选择 200 个最近同步的 HTTP/HTTPS 镜像，然后根据下载速度进行排序，最后将结果覆写到 /etc/pacman.d/mirrorlist 文件内](#%E9%80%89%E6%8B%A9-200-%E4%B8%AA%E6%9C%80%E8%BF%91%E5%90%8C%E6%AD%A5%E7%9A%84-httphttps-%E9%95%9C%E5%83%8F%E7%84%B6%E5%90%8E%E6%A0%B9%E6%8D%AE%E4%B8%8B%E8%BD%BD%E9%80%9F%E5%BA%A6%E8%BF%9B%E8%A1%8C%E6%8E%92%E5%BA%8F%E6%9C%80%E5%90%8E%E5%B0%86%E7%BB%93%E6%9E%9C%E8%A6%86%E5%86%99%E5%88%B0-etcpacmandmirrorlist-%E6%96%87%E4%BB%B6%E5%86%85)
    - [选择在最近 12 小时内同步的，并且是位于指定国家的镜像，然后根据下载速度进行排序，最后将结果覆写到 /etc/pacman.d/mirrorlist 文件内](#%E9%80%89%E6%8B%A9%E5%9C%A8%E6%9C%80%E8%BF%91-12-%E5%B0%8F%E6%97%B6%E5%86%85%E5%90%8C%E6%AD%A5%E7%9A%84%E5%B9%B6%E4%B8%94%E6%98%AF%E4%BD%8D%E4%BA%8E%E6%8C%87%E5%AE%9A%E5%9B%BD%E5%AE%B6%E7%9A%84%E9%95%9C%E5%83%8F%E7%84%B6%E5%90%8E%E6%A0%B9%E6%8D%AE%E4%B8%8B%E8%BD%BD%E9%80%9F%E5%BA%A6%E8%BF%9B%E8%A1%8C%E6%8E%92%E5%BA%8F%E6%9C%80%E5%90%8E%E5%B0%86%E7%BB%93%E6%9E%9C%E8%A6%86%E5%86%99%E5%88%B0-etcpacmandmirrorlist-%E6%96%87%E4%BB%B6%E5%86%85)
- [自动处理](#%E8%87%AA%E5%8A%A8%E5%A4%84%E7%90%86)
    - [systemd service](#systemd-service)
    - [pacman hook](#pacman-hook)
    - [Cron task](#cron-task)

<!-- /TOC -->

# 安装reflector
```
> pacman -S reflector
```

# 用法
## 根据下载速度进行排序，并筛选出前 5 个最近同步的镜像，最后将结果覆写到 /etc/pacman.d/mirrorlist 文件内
```
> reflector --verbose --latest 5 --sort rate --save /etc/pacman.d/mirrorlist
```

## 选择 200 个最近同步的 HTTP/HTTPS 镜像，然后根据下载速度进行排序，最后将结果覆写到 /etc/pacman.d/mirrorlist 文件内
```
> reflector --latest 200 --protocol http --protocol https --sort rate --save /etc/pacman.d/mirrorlist
```

## 选择在最近 12 小时内同步的，并且是位于指定国家的镜像，然后根据下载速度进行排序，最后将结果覆写到 /etc/pacman.d/mirrorlist 文件内
```
> reflector --country China --age 12 --protocol https --sort rate --save /etc/pacman.d/mirrorlist
```

# 自动处理
## systemd service
Reflector 附带了一个可启用的 `reflector.service` 服务文件。
该服务会根据 `/etc/xdg/reflector/reflector.conf` 文件所指定的参数运行 `Reflector` 脚本。该配置文件包含了 `Reflector` 运行时所需的所有命令行参数。这些参数可以用一行或者多行来表示，并且允许空白行和以 `#` 开头的注释行。可以从默认配置文件开始进行自定义配置。

例如，从中国的镜像中筛选出 5 个最新的并且支持 HTTPS 的镜像，然后将结果覆写到 /etc/pacman.d/mirrorlist 文件内；使用：
```
/etc/xdg/reflector/reflector.conf
--save /etc/pacman.d/mirrorlist
--country China
--protocol https
--latest 5
```
启用 reflector.service 服务可以在引导时运行 Reflector 脚本。要立即运行，启动该服务。

## pacman hook
你可以创建一个 pacman 挂钩来启动 reflector.service 服务，并且在更新 pacman-mirrorlist 软件包后删除所创建的 .pacnew 文件。
```
/etc/pacman.d/hooks/mirrorupgrade.hook
[Trigger]
Operation = Upgrade
Type = Package
Target = pacman-mirrorlist

[Action]
Description = Updating pacman-mirrorlist with reflector and removing pacnew...
When = PostTransaction
Depends = reflector
Exec = /bin/sh -c 'systemctl start reflector.service; if [ -f /etc/pacman.d/mirrorlist.pacnew ]; then rm /etc/pacman.d/mirrorlist.pacnew; fi'
```
像服务一节所说那样编辑 /etc/xdg/reflector/reflector.conf 文件，从而设置好所需的镜像选项。

## Cron task
要每天更新镜像列表，参考如下内容：
```
/etc/cron.daily/mirrorlist
#!/bin/bash

# Get the country thing
/usr/bin/reflector -c "India" -p http --sort rate > /etc/pacman.d/mirrorlist

# Work through the alternatives
/usr/bin/reflector -p http  --latest 20 -p https -p ftp --sort rate >> /etc/pacman.d/mirrorlist
```
