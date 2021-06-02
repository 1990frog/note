[TOC]

使用单元
一个单元配置文件可以描述如下内容之一：系统服务（.service）、挂载点（.mount）、sockets（.sockets） 、系统设备（.device）、交换分区（.swap）、文件路径（.path）、启动目标（.target）、由 systemd 管理的计时器（.timer）。详情参阅 systemd.unit(5) 。

使用 systemctl 控制单元时，通常需要使用单元文件的全名，包括扩展名（例如 sshd.service ）。但是有些单元可以在 systemctl 中使用简写方式。

如果无扩展名，systemctl 默认把扩展名当作 .service 。例如 netcfg 和 netcfg.service 是等价的。
挂载点会自动转化为相应的 .mount 单元。例如 /home 等价于 home.mount 。
设备会自动转化为相应的 .device 单元，所以 /dev/sda2 等价于 dev-sda2.device 。
注意： 有一些单元的名称包含一个 @ 标记（例如： name@string.service ），这意味着它是模板单元 name@.service 的一个 实例。 string 被称作实例标识符，在 systemctl 调用模板单元时，会将其当作一个参数传给模板单元，模板单元会使用这个传入的参数代替模板中的 %I 指示符。
在实例化之前，systemd 会先检查 name@string.suffix 文件是否存在（如果存在，就直接使用这个文件，而不是模板实例化）。大多数情况下，包含 @ 标记都意味着这个文件是模板。如果一个模板单元没有实例化就调用，该调用会返回失败，因为模板单元中的 %I 指示符没有被替换。

提示：
下面的大部分命令都可以跟多个单元名, 详细信息参见 systemctl(1)。
systemctl命令在enable、disable和mask子命令中增加了--now选项，可以实现激活的同时启动服务，取消激活的同时停止服务。
一个软件包可能会提供多个不同的单元。如果你已经安装了软件包，可以通过pacman -Qql package | grep systemd命令检查这个软件包提供了哪些单元。


显示 系统状态：

$ systemctl status
输出激活的单元：

$ systemctl
以下命令等效：

$ systemctl list-units
输出运行失败的单元：

$ systemctl --failed
所有可用的单元文件存放在 /usr/lib/systemd/system/ 和 /etc/systemd/system/ 目录（后者优先级更高）。查看所有已安装服务：

$ systemctl list-unit-files
显示 cgroup slice, 内存和父 PID:

$ systemctl status pid

立即激活单元：

# systemctl start <单元>
立即停止单元：

# systemctl stop <单元>
重启单元：

# systemctl restart <单元>
重新加载配置：

# systemctl reload <单元>
输出单元运行状态：

$ systemctl status <单元>
检查单元是否配置为自动启动：

$ systemctl is-enabled <单元>
开机自动激活单元：

# systemctl enable <单元>
设置单元为自动启动并立即启动这个单元:

# systemctl enable --now unit
取消开机自动激活单元：

# systemctl disable <单元>
禁用一个单元（禁用后，间接启动也是不可能的）：

# systemctl mask <单元>
取消禁用一个单元：

# systemctl unmask <单元>
显示单元的手册页（必须由单元文件提供）：

# systemctl help <单元>
重新载入 systemd 系统配置，扫描单元文件的变动。注意这里不会重新加载变更的单元文件。参考上面的 reload 示例。

# systemctl daemon-reload
