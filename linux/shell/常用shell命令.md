
# ps -ef
-e 显示所有进程。
-f 全格式。
-h 不显示标题。
-l 长格式。
-w 宽输出。

a 显示终端上的所有进程，包括其他用户的进程。
r 只显示正在运行的进程。
x 显示没有控制终端的进程。
ps aux 是用BSD的格式来显示 java这个进程
显示的项目有：USER , PID , %CPU , %MEM , VSZ , RSS , TTY , STAT , START , TIME , COMMAND
ps -ef 是用标准的格式显示java这个进程
显示的项目有：UID , PID , PPID , C , STIME , TTY , TIME , CMD

格式说明：

USER: 行程拥有者

PID: pid

%CPU: 占用的 CPU 使用率

%MEM: 占用的记忆体使用率

VSZ: 占用的虚拟记忆体大小

RSS: 占用的记忆体大小

TTY: 终端的次要装置号码 (minor device number of tty)

STAT: 该行程的状态，linux的进程有5种状态：

D 不可中断 uninterruptible sleep (usually IO)

R 运行 runnable (on run queue)

S 中断 sleeping

T 停止 traced or stopped

Z 僵死 a defunct (”zombie”) process

注: 其它状态还包括W(无驻留页), <(高优先级进程), N(低优先级进程), L(内存锁页).

START: 行程开始时间

TIME: 执行的时间

COMMAND:所执行的指令

ps命令
1）ps a 显示现行终端机下的所有程序，包括其他用户的程序。
2）ps -A 显示所有程序。
3）ps c 列出程序时，显示每个程序真正的指令名称，而不包含路径，参数或常驻服务的标示。
4）ps -e 此参数的效果和指定"A"参数相同。
5）ps e 列出程序时，显示每个程序所使用的环境变量。
6）ps f 用ASCII字符显示树状结构，表达程序间的相互关系。
7）ps -H 显示树状结构，表示程序间的相互关系。
8）ps -N 显示所有的程序，除了执行ps指令终端机下的程序之外。
9）ps s 采用程序信号的格式显示程序状况。
10）ps S 列出程序时，包括已中断的子程序资料。
11）ps -t <终端机编号> 　指定终端机编号，并列出属于该终端机的程序的状况。
12）ps u 　 以用户为主的格式来显示程序状况。
13）ps x 　 显示所有程序，不以终端机来区分。
14）ps -l 详细显示该PID的信息




关注Linux的系统状态，主要从两个角度出发：

一个角度是系统正在运行什么服务（ps命令）；

另外一个就是有什么连接或服务可用（netstat命令）。

netstat还可以显示ps无法显示的、从inetd或xinetd中运行的服务，比如telnet等。

 
一、ps -ef 命令和ps -aux命令
1.1、ps -ef | grep详解

ps命令将某个进程显示出来

grep命令是查找

中间的|是管道命令 是指ps命令与grep同时执行

PS是LINUX下最常用的也是非常强大的进程查看命令

ps -e 此参数的效果和指定"A"参数相同。

ps f 用ASCII字符显示树状结构，表达程序间的相互关系。 

grep命令是查找，是一种强大的文本搜索工具，它能使用正则表达式搜索文本，并把匹配的行打印出来。

grep全称是Global Regular Expression Print，表示全局正则表达式版本，它的使用权限是所有用户。

以下这条命令是检查java 进程是否存在：ps -ef |grep java

字段含义如下：
UID       PID       PPID      C     STIME    TTY       TIME         CMD

zzw      14124   13991      0     00:38      pts/0      00:00:00    grep --color=auto dae

 

UID      ：程序被该 UID 所拥有

PID      ：就是这个程序的 ID 

PPID    ：则是其上级父程序的ID

C          ：CPU使用的资源百分比

STIME ：系统启动时间

TTY     ：登入者的终端机位置

TIME   ：使用掉的CPU时间。

CMD   ：所下达的是什么指令
 
1.2 ps -aux | grep命令

ps是显示当前状态处于running的进程，grep表示在这些里搜索，而ps aux是显示所有进程和其状态。

$ ps aux | grep amoeba        查到amoeba的进程

ps aux输出格式：

USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND

 

格式说明：

USER: 行程拥有者

PID: pid

%CPU: 占用的 CPU 使用率

%MEM: 占用的记忆体使用率

VSZ: 占用的虚拟记忆体大小

RSS: 占用的记忆体大小

TTY: 终端的次要装置号码 (minor device number of tty)

 

STAT: 该行程的状态，linux的进程有5种状态：

D 不可中断 uninterruptible sleep (usually IO)

R 运行 runnable (on run queue)

S 中断 sleeping

T 停止 traced or stopped

Z 僵死 a defunct (”zombie”) process

注: 其它状态还包括W(无驻留页), <(高优先级进程), N(低优先级进程), L(内存锁页).

START: 行程开始时间

TIME: 执行的时间

COMMAND:所执行的指令

1) ps a 显示现行终端机下的所有程序，包括其他用户的程序。
2）ps -A 显示所有程序。 
3）ps c 列出程序时，显示每个程序真正的指令名称，而不包含路径，参数或常驻服务的标示。 
4）ps -e 此参数的效果和指定"A"参数相同。 
5）ps e 列出程序时，显示每个程序所使用的环境变量。 
6）ps f 用ASCII字符显示树状结构，表达程序间的相互关系。 
7）ps -H 显示树状结构，表示程序间的相互关系。 
8）ps -N 显示所有的程序，除了执行ps指令终端机下的程序之外。 
9）ps s 采用程序信号的格式显示程序状况。 
10）ps S 列出程序时，包括已中断的子程序资料。 
11）ps -t 　指定终端机编号，并列出属于该终端机的程序的状况。 
12）ps u 　以用户为主的格式来显示程序状况。 
13）ps x 　显示所有程序，不以终端机来区分。
二、netstat -apn命令

netstat -anp查看端口占用情况

-a，显示所有

-n，不用别名显示，只用数字显示

-p，显示进程号和进程名
