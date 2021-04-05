[TOC]

# 配置文件
内核相关参数（/etc/sysctl.conf）
资源限制（/etc/security/limit.conf）
# 网络相关参数
net.core.somaxconn=65535
net.core.netdev_max_backlog=65535

net.ipv4.tcp_max_syn_backlog=65535
net.ipv4.tcp_fin_timeout=10
net.ipv4.tcp_tw_reuse=0
net.ipv4.tcp_tw_recycle=1

net.core.wmen_default=87380
net.core.wmen_max=16777216
net.core.rmem_default=87380
net.core.rmem_max=16777216

net.ipv4.tcp_keepalive_time=120
net.ipv4.tcp_keepalive_intvl=30
net.ipv4.tcp_keepalive_probes=3

Linux内存参数中最重要的参数之一，用于定义内存段的最大值
这个参数应该设置的足够大，以便能在一个共享内存段下容纳下整个的Innodb缓冲池的大小
这个值的大小对于64位linux系统，可取的最大值为物理内存值减1byte，建议值为大于物理内存的一半，一般取值大于Innodb缓冲池的大小即可，可以取物理内存减1byte。
kernel.shmmax=4294967295

如果我们使用free-m在系统中查看可以看到类似下面的内容其中swap就是交换分区
当操作系统因为没有足够的内存时就会将一些虚拟内存写到磁盘的交换区中这样就会发生内存交换
vm.swappiness=0

# 增加资源限制（/etc/security/limit.conf）
```
* soft nproc 65535    #可打开的文件描述符的最大数(软限制)
* hard nproc 65535    #可打开的文件描述符的最大数(硬限制)
* soft nofile 65535    #单个用户可用的最大进程数量(软限制)
* hard nofile 65535    #单个用户可用的最大进程数量(硬限制)
```
# 磁盘调度策略（/sys/block/devname/queue/scheduler）
cat /sys/block/sda/queue/scheduler
```
noop anticipatory deadline [cfq]
```
## noop（电梯式调度策略）：
NOOP实现了一个FIFO队列，它像电梯的工作方法一样对I/O请求进行组织，当有一个新的请求到来时，它将请求合并到最近的请求之后，以此来保证请求同一介质。NOOP倾向饿死读而利于写，因此NOOP对于闪存设备、RAM及嵌入式系统是最好的选择。
## deadline（截止时间调度策略）
deadline确保了在一个截止时间内服务请求，这个截止时间是可调整的，而默认读期限短于写期限。这样就防止了写操作因为不能被读取而饿死的现象，deadline对数据库类应用是最好的选择。
## anticipatory（预计I/O调度策略）
本质上与deadline一样，但在最后一次读操作后，要等待6ms，才能继续进行对其他I/O操作，而会将一些小写入流合并成一个大写入流，用写入延时换取最大的写入吞吐量。AS适合于写入较多的环境，比如文件服务器，AS对数据库环境表现很差。

# 文件系统对性能的影响
Windows
+ FAT
+ NTFS

Linux
+ EXT3
+ EXT4
+ XFS

# EXT3/4系统的挂载参数（/etc/fstab）
```
data=writeback|ordered|journal
noatiome,nodiratime
/dev/sda1/ext4 noatiome,nodiratime,data=writeback 1 1
```
