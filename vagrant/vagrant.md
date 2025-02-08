<!-- TOC -->

- [查看状态](#%E6%9F%A5%E7%9C%8B%E7%8A%B6%E6%80%81)
- [查看ssh](#%E6%9F%A5%E7%9C%8Bssh)
- [修改内存](#%E4%BF%AE%E6%94%B9%E5%86%85%E5%AD%98)
- [常用命令](#%E5%B8%B8%E7%94%A8%E5%91%BD%E4%BB%A4)
    - [box 管理box镜像box是创建虚拟机的模板](#box-%E7%AE%A1%E7%90%86box%E9%95%9C%E5%83%8Fbox%E6%98%AF%E5%88%9B%E5%BB%BA%E8%99%9A%E6%8B%9F%E6%9C%BA%E7%9A%84%E6%A8%A1%E6%9D%BF)
    - [init 初始化项目目录，将在当前目录下生成Vagrantfile文件](#init-%E5%88%9D%E5%A7%8B%E5%8C%96%E9%A1%B9%E7%9B%AE%E7%9B%AE%E5%BD%95%E5%B0%86%E5%9C%A8%E5%BD%93%E5%89%8D%E7%9B%AE%E5%BD%95%E4%B8%8B%E7%94%9F%E6%88%90vagrantfile%E6%96%87%E4%BB%B6)
    - [up 启动虚拟机，第一次执行将创建并初始化并启动虚拟机](#up-%E5%90%AF%E5%8A%A8%E8%99%9A%E6%8B%9F%E6%9C%BA%E7%AC%AC%E4%B8%80%E6%AC%A1%E6%89%A7%E8%A1%8C%E5%B0%86%E5%88%9B%E5%BB%BA%E5%B9%B6%E5%88%9D%E5%A7%8B%E5%8C%96%E5%B9%B6%E5%90%AF%E5%8A%A8%E8%99%9A%E6%8B%9F%E6%9C%BA)
    - [reload 重启虚拟机](#reload-%E9%87%8D%E5%90%AF%E8%99%9A%E6%8B%9F%E6%9C%BA)
    - [halt 将虚拟机关机](#halt-%E5%B0%86%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%85%B3%E6%9C%BA)
    - [destroy 删除虚拟机（包括虚拟机文件）](#destroy-%E5%88%A0%E9%99%A4%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%8C%85%E6%8B%AC%E8%99%9A%E6%8B%9F%E6%9C%BA%E6%96%87%E4%BB%B6)
    - [suspend 暂停休眠、挂起虚拟机](#suspend-%E6%9A%82%E5%81%9C%E4%BC%91%E7%9C%A0%E6%8C%82%E8%B5%B7%E8%99%9A%E6%8B%9F%E6%9C%BA)
    - [resume 恢复已暂停休眠、挂起的虚拟机](#resume-%E6%81%A2%E5%A4%8D%E5%B7%B2%E6%9A%82%E5%81%9C%E4%BC%91%E7%9C%A0%E6%8C%82%E8%B5%B7%E7%9A%84%E8%99%9A%E6%8B%9F%E6%9C%BA)
    - [snapshot 管理虚拟机快照hyperv中叫检查点](#snapshot-%E7%AE%A1%E7%90%86%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%BF%AB%E7%85%A7hyperv%E4%B8%AD%E5%8F%AB%E6%A3%80%E6%9F%A5%E7%82%B9)
    - [status 列出当前目录Vagrantfile所在目录下安装的虚拟机列表及它们的状态](#status-%E5%88%97%E5%87%BA%E5%BD%93%E5%89%8D%E7%9B%AE%E5%BD%95vagrantfile%E6%89%80%E5%9C%A8%E7%9B%AE%E5%BD%95%E4%B8%8B%E5%AE%89%E8%A3%85%E7%9A%84%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%88%97%E8%A1%A8%E5%8F%8A%E5%AE%83%E4%BB%AC%E7%9A%84%E7%8A%B6%E6%80%81)
    - [global-status 列出全局已安装虚拟机列表及它们的状态](#global-status-%E5%88%97%E5%87%BA%E5%85%A8%E5%B1%80%E5%B7%B2%E5%AE%89%E8%A3%85%E8%99%9A%E6%8B%9F%E6%9C%BA%E5%88%97%E8%A1%A8%E5%8F%8A%E5%AE%83%E4%BB%AC%E7%9A%84%E7%8A%B6%E6%80%81)
    - [ssh 通过ssh连接虚拟机](#ssh-%E9%80%9A%E8%BF%87ssh%E8%BF%9E%E6%8E%A5%E8%99%9A%E6%8B%9F%E6%9C%BA)
    - [ssh-config 输出ssh连接虚拟机时使用的配置项](#ssh-config-%E8%BE%93%E5%87%BAssh%E8%BF%9E%E6%8E%A5%E8%99%9A%E6%8B%9F%E6%9C%BA%E6%97%B6%E4%BD%BF%E7%94%A8%E7%9A%84%E9%85%8D%E7%BD%AE%E9%A1%B9)
    - [port 查看各虚拟机映射的端口列表hyperv不支持该功能](#port-%E6%9F%A5%E7%9C%8B%E5%90%84%E8%99%9A%E6%8B%9F%E6%9C%BA%E6%98%A0%E5%B0%84%E7%9A%84%E7%AB%AF%E5%8F%A3%E5%88%97%E8%A1%A8hyperv%E4%B8%8D%E6%94%AF%E6%8C%81%E8%AF%A5%E5%8A%9F%E8%83%BD)
- [vagrant 网络](#vagrant-%E7%BD%91%E7%BB%9C)
    - [private_network](#private_network)
    - [public_network](#public_network)
- [config.vm.synced_folder](#configvmsynced_folder)
- [文档](#%E6%96%87%E6%A1%A3)
- [boxes](#boxes)

<!-- /TOC -->

手动ssh连接
vagrant ssh-config

```
ost default
  HostName 127.0.0.1
  User vagrant
  Port 2222
  UserKnownHostsFile /dev/null
  StrictHostKeyChecking no
  PasswordAuthentication no
  IdentityFile /path/to/private/key
  IdentitiesOnly yes
  LogLevel FATAL
```

ssh vagrant@127.0.0.1 -p 2222 -i /path/to/private/key

多虚拟机环境
vagrant ssh vm1

退出
exit

## IdentityFile
在 Vagrant 中，IdentityFile 是 SSH 连接时使用的私钥文件路径。Vagrant 默认会为每个虚拟机生成一个唯一的 SSH 密钥对，并将私钥文件存储在 .vagrant/machines/<vm-name>/<provider>/private_key 路径下。

以下是关于 IdentityFile 的详细信息以及如何使用它：
```bash
vagrant ssh-config

Host default
  HostName 127.0.0.1
  User vagrant
  Port 2222
  UserKnownHostsFile /dev/null
  StrictHostKeyChecking no
  PasswordAuthentication no
  IdentityFile /path/to/your/project/.vagrant/machines/default/virtualbox/private_key
  IdentitiesOnly yes
  LogLevel FATAL
```

IdentityFile 是 Vagrant 自动生成的私钥文件路径。
User 是 SSH 连接的用户名（默认是 vagrant）。
HostName 和 Port 是虚拟机的地址和端口。


2. 手动使用 IdentityFile 进行 SSH 连接
如果你不想使用 vagrant ssh，而是想手动通过 SSH 连接到虚拟机，可以使用 IdentityFile 中的私钥文件。例如：
```bash
ssh -i /path/to/private_key vagrant@127.0.0.1 -p 2222
```
-i 参数指定私钥文件路径。
vagrant 是默认的 SSH 用户名。
127.0.0.1 和 2222 是虚拟机的地址和端口（可以从 vagrant ssh-config 中获取）。

3. 自定义 IdentityFile

如果你想使用自定义的 SSH 密钥对，而不是 Vagrant 自动生成的密钥，可以在 Vagrantfile 中配置 config.ssh.private_key_path。例如：

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "your-box-name"
  
  # 使用自定义的私钥文件
  config.ssh.private_key_path = "~/.ssh/my_private_key"
  
  # 如果需要，也可以指定公钥文件
  config.ssh.insert_key = false
end
```
    config.ssh.private_key_path 指定自定义的私钥文件路径。

    config.ssh.insert_key = false 表示不自动插入 Vagrant 的默认密钥。

4. 多虚拟机环境中的 IdentityFile
如果你的 Vagrantfile 中定义了多个虚拟机，每个虚拟机都会有自己的 IdentityFile。你可以通过 vagrant ssh-config <vm-name> 查看特定虚拟机的 SSH 配置。例如：
```bash
vagrant ssh-config vm1
```

5. 默认的 IdentityFile 路径

Vagrant 默认的 IdentityFile 路径通常位于：
复制

.vagrant/machines/<vm-name>/<provider>/private_key

    <vm-name> 是虚拟机的名称（默认为 default）。

    <provider> 是使用的 provider（如 virtualbox、vmware 等）。

    6. 注意事项

    确保私钥文件的权限正确（通常为 600）。

    如果你修改了 Vagrantfile 中的 SSH 配置，需要运行 vagrant reload 或 vagrant provision 使更改生效。
# 查看状态
vagrant status

# 查看ssh
vagrant ssh-config




# 修改内存
```ruby
vim Vagrant

Vagrant.configure("2") do |config|
  config.vm.box = "your-box-name"
  
  # 配置虚拟机内存
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end
end
```


--------

在 Vagrant 中，如果你的 Vagrantfile 配置了多个虚拟机，你可以通过以下几种方式在这些虚拟机之间进行 SSH 连接：
1. 使用 vagrant ssh 连接到指定虚拟机

在 Vagrantfile 中定义了多个虚拟机时，可以通过 vagrant ssh <vm-name> 连接到指定的虚拟机。例如：
bash
复制

vagrant ssh vm1
vagrant ssh vm2

其中 vm1 和 vm2 是你在 Vagrantfile 中定义的虚拟机名称。
2. 在虚拟机之间 SSH 连接

如果你已经通过 vagrant ssh 连接到其中一个虚拟机，并希望从这个虚拟机 SSH 连接到另一个虚拟机，可以按照以下步骤操作：
步骤 1：获取目标虚拟机的 IP 地址

在 Vagrantfile 中，确保为每个虚拟机配置了网络（如私有网络或公有网络）。例如：
ruby
复制

Vagrant.configure("2") do |config|
  config.vm.define "vm1" do |vm1|
    vm1.vm.box = "ubuntu/focal64"
    vm1.vm.network "private_network", ip: "192.168.56.10"
  end

  config.vm.define "vm2" do |vm2|
    vm2.vm.box = "ubuntu/focal64"
    vm2.vm.network "private_network", ip: "192.168.56.20"
  end
end

    vm1 的 IP 地址为 192.168.56.10。

    vm2 的 IP 地址为 192.168.56.20。

步骤 2：在虚拟机之间 SSH 连接

假设你已经通过 vagrant ssh vm1 连接到 vm1，然后可以从 vm1 SSH 连接到 vm2：
bash
复制

ssh vagrant@192.168.56.20

    默认的 SSH 用户名是 vagrant。

    默认的 SSH 密码也是 vagrant（如果没有禁用密码登录）。

3. 使用 SSH 密钥连接

Vagrant 默认会为每个虚拟机生成一个 SSH 密钥对。你可以使用这些密钥在虚拟机之间进行无密码 SSH 连接。
步骤 1：获取目标虚拟机的私钥

在主机上运行以下命令，查看目标虚拟机（如 vm2）的私钥路径：
bash
复制

vagrant ssh-config vm2

输出示例：
复制

Host vm2
  HostName 192.168.56.20
  User vagrant
  Port 22
  IdentityFile /path/to/your/project/.vagrant/machines/vm2/virtualbox/private_key

步骤 2：将私钥复制到源虚拟机

将 vm2 的私钥文件复制到 vm1 中。例如，在主机上运行：
bash
复制

scp -i /path/to/vm1/private_key /path/to/vm2/private_key vagrant@192.168.56.10:/home/vagrant/.ssh/vm2_private_key

步骤 3：在 vm1 中配置 SSH

在 vm1 中，将私钥文件权限设置为 600，并配置 SSH 连接：
bash
复制

chmod 600 ~/.ssh/vm2_private_key
ssh -i ~/.ssh/vm2_private_key vagrant@192.168.56.20

4. 使用 vagrant ssh 跳板连接

如果你不想手动复制密钥，可以通过 vagrant ssh 跳板连接到目标虚拟机。例如：
bash
复制

vagrant ssh vm1 -- ssh vagrant@192.168.56.20

5. 配置 SSH 免密登录（可选）

为了方便，你可以在虚拟机之间配置 SSH 免密登录：
步骤 1：在 vm1 中生成 SSH 密钥

在 vm1 中运行以下命令生成 SSH 密钥对：
bash
复制

ssh-keygen -t rsa -b 4096

将公钥保存到默认路径（如 ~/.ssh/id_rsa.pub）。
步骤 2：将公钥复制到 vm2

将 vm1 的公钥复制到 vm2 的 ~/.ssh/authorized_keys 文件中：
bash
复制

ssh-copy-id vagrant@192.168.56.20

步骤 3：测试免密登录

现在，你可以从 vm1 直接 SSH 连接到 vm2，而无需输入密码：
bash
复制

ssh vagrant@192.168.56.20

总结

    使用 vagrant ssh <vm-name> 连接到指定虚拟机。

    在虚拟机之间通过 IP 地址和 SSH 密钥进行连接。

    可以配置 SSH 免密登录以简化操作。

如果你有更多问题，欢迎随时提问！


同时构建多台
修改Vagrantfile

修改之前产生的Vagrantfile文件为

Vagrant.configure("2") do |config|
  
  config.vm.define "centos7-1" do |vb|
      config.vm.provider "virtualbox" do |v|
      v.memory = 1024
      v.cpus = 1
    end
  vb.vm.host_name = "centos7-1"
  vb.vm.network "private_network", ip: "192.168.56.111"
  vb.vm.box = "centos7.2"
  end

  config.vm.define "centos7-2" do |vb1|
      config.vm.provider "virtualbox" do |v|
      v.memory = 1024
      v.cpus = 1
    end
  vb1.vm.host_name = "centos7-2"
  vb1.vm.network "private_network", ip: "192.168.56.112"
  vb1.vm.box = "centos7.2"
  end

  config.vm.define "centos7-3" do |vb2|
      config.vm.provider "virtualbox" do |v|
      v.memory = 1024
      v.cpus = 1
    end
  vb2.vm.host_name = "centos7-3"
  vb2.vm.network "private_network", ip: "192.168.56.113"
  vb2.vm.box = "centos7.2"
  end
end

网络使用的是私有网络，私有网络和公有网络区别可以看下文

---

# 常用命令
## box 管理box镜像(box是创建虚拟机的模板)
```bash
vagrant box add centos/7
```

## init 初始化项目目录，将在当前目录下生成Vagrantfile文件
```bash
vagrant init centos/7
```

## up 启动虚拟机，第一次执行将创建并初始化并启动虚拟机
```bash
vagrant up
```

## reload 重启虚拟机
```bash
vagrant reload
```

## halt 将虚拟机关机
```bash
vagrant reload
```

## destroy 删除虚拟机（包括虚拟机文件）
```bash
vagrant destroy
```

## suspend 暂停(休眠、挂起)虚拟机
```bash
vagrant suspend
```

## resume 恢复已暂停(休眠、挂起)的虚拟机
```bash
vagrant resume
```

## snapshot 管理虚拟机快照(hyperv中叫检查点)
```bash
vagrant shapshot -h
Available subcommands:
     delete
     list
     pop
     push
     restore
     save

For help on any individual subcommand run `vagrant snapshot <subcommand> -h`
        --[no-]color                 Enable or disable color output
        --machine-readable           Enable machine readable output
    -v, --version                    Display Vagrant version
        --debug                      Enable debug output
        --timestamp                  Enable timestamps on log output
        --debug-timestamp            Enable debug output with timestamps
        --no-tty                     Enable non-interactive output
```
## status 列出当前目录(Vagrantfile所在目录)下安装的虚拟机列表及它们的状态
```bash
vagrant status
```

## global-status 列出全局已安装虚拟机列表及它们的状态
```bash
vagrant global-status
```

## ssh 通过ssh连接虚拟机
```bash
vagrant ssh
vagrant ssh vm1
```

## ssh-config 输出ssh连接虚拟机时使用的配置项
```bash

```

## port 查看各虚拟机映射的端口列表(hyperv不支持该功能)

# vagrant 网络
## private_network
私有网络，对应于virtualbox的host-only网络模型，这种模型下，虚拟机之间和宿主机(的虚拟网卡)之间可以互相通信，但不在该网络内的设备无法访问虚拟机

如果私有网络的虚机不在一个网络，vagrant为这些private_network网络配置的IP地址并不在同一个网段。vagrant会自动为不同网段创建对应的host-only网络。

所以使用private_network如果没有外部机器(虚拟机宿主机之外的机器)连接，使用这种方式设置的静态ip，能够摆脱主机网络变换的限制。

```
vb1.vm.network "private_network", ip: "192.168.56.2"
```

## public_network
公有网络，对应于virtualbox的桥接模式，这种模式下，虚拟机的网络和宿主机的物理网卡是平等的，它们在同一个网络内，虚拟机可以访问外网，外界网络(特指能访问物理网卡的设备)也能访问虚拟机

vagrant为virtualbox配置的public_network，其本质是将虚拟机加入到了virtualbox的桥接网络内。

vagrant在将虚拟机的网卡加入桥接网络时，默认会交互式地询问用户要和哪个宿主机上的网卡进行桥接，一般来说，应该选择可以上外网的物理设备进行桥接。

由于需要非交互式选择或者需要先指定要桥接的设备名，而且不同用户的网络环境不一样，因此如非必要，一般不在vagrant中为虚拟机配置public_network。

公有网络的iP网络要和主机的网段一致。


# config.vm.synced_folder
用于将主机（Host）上的目录同步到虚拟机（Guest）中。这对于开发环境非常有用，因为你可以在主机上编辑代码，同时在虚拟机中运行和测试代码。

语法
config.vm.synced_folder "主机目录", "虚拟机目录", 选项


# 文档
https://developer.hashicorp.com/vagrant/docs




# boxes
https://portal.cloud.hashicorp.com/vagrant/discover



https://www.bilibili.com/video/BV14A411u79f?spm_id_from=333.788.videopod.sections&vd_source=75b5a4665a5280dc40c714fc1ad5c04b