
sudo pacman -S ntp


ntpdate time.windows.com

date -s "2015-07-15 22:13:30"

hwclock --systohc   (表示系统时间同步到硬件时钟)

hwclock --hctosys (表示硬件时钟同步到系统时间)

2、根据互联网时间同步：

首先查看linux是否有ntp这个软件：

rpm -qa | grep ntp

如果没安装继续查找：

yum search ntp

然后通过上面查找的信息提示来安装这个ntp：

yum install ntp.i386

完成安装后：输入ntp，按tab键进入提示，会有ntpdate，我们就需要它

开始进行同步：

ntpdate time.windows.com

这样就行了，很简单吧，，说明一下，time.windows.com是windows的时间服务器

最后在把系统时间同步到硬件时钟：

hwclock --systohc

互联网同步就完成了！

3、上面两种太麻烦，因为ntp有一个守护进程启动就可以同步了

service ntpd start

然后回车后在查看一下:ps -ef | grep nepd

以下是同步后还是不对的，请继续往下看：

1、输入 date -R

看看是否是加8  (+0800)

2、如何没有+8

设置linux时区：

输入：tzselect

选择序号：5代表Asia

然后再选国家：9 代表中国

然后在选1

就把时区调整过来了

以上就是同步时间的方法

