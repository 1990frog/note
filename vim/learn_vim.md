[TOC]

# 打开vim
vim
vim xxx.file

一次打开多个文件
vim x1.file x2.file

# 退出vim
:quit
:q
:q! 强制退出

# 保存文件
:write
:w
:w new.file
如果这是一个新建的文件，您必须给出文件名才能保存。

# 参数
vim --version


如果您想打开hello.txt文件后迅速执行一条命令，您可以向vim传递一个+{cmd}选项。
vim +%s/pancake/bagel/g hello.txt

该命令可以叠加
vim +%s/pancake/bagel/g +%s/bagel/egg/g +%s/egg/donut/g hello.txt

另一种写法 -c
vim -c %s/pancake/bagel/g hello.txt
vim -c %s/pancake/bagel/g +%s/bagel/egg/g +%s/egg/donut/g hello.txt


# 打开多个窗口
您可以使用o和O选项使Vim打开后分别显示为水平或垂直分割的窗口。

vim -o2 打开两个水平分割的窗口
vim -O2 打开两个垂直分割的窗口

若想将Vim打开为5个水平分割的窗口，并使前两个窗口显示hello1.txt和hello2.txt的内容，在终端中运行：
vim -o5 hello1.txt hello2.txt

# 挂起
如果您编辑时想将Vim挂起，您可以按下Ctrl-z。同样，您也可以使用:stop或:suspend命令达到相同的效果。若想从挂起状态返回，在终端中运行fg命令。

