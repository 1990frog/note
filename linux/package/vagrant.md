<!-- TOC -->

- [前提](#%E5%89%8D%E6%8F%90)
- [添加box（镜像）](#%E6%B7%BB%E5%8A%A0box%E9%95%9C%E5%83%8F)
- [初始化](#%E5%88%9D%E5%A7%8B%E5%8C%96)
- [启动](#%E5%90%AF%E5%8A%A8)
- [停止](#%E5%81%9C%E6%AD%A2)
- [销毁](#%E9%94%80%E6%AF%81)
- [打开tty](#%E6%89%93%E5%BC%80tty)
- [查看状态](#%E6%9F%A5%E7%9C%8B%E7%8A%B6%E6%80%81)
- [查看ssh](#%E6%9F%A5%E7%9C%8Bssh)

<!-- /TOC -->
# 前提
virtualbox

# 添加box（镜像）
vagrant box add centos/7

# 初始化
vagrant init centos/7

# 启动
vagrant up

# 停止
vagrant halt

# 销毁
vagrant destroy

# 连接虚拟机
vagrant ssh

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