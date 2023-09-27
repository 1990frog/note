[TOC]

[Learn-Vim_zh_cn](https://github.com/wsdjeg/Learn-Vim_zh_cn/tree/master)

# ch01
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


# 02
在Vim中，Buffers缓冲区，Windows窗口，Tabs选项卡

在开始之前，确保您的vimrc文件中开启了set hidden选项。若没有配置该选项，当您想切换buffer且当前buffer没有保存时，Vim将提示您保存文件（如果您想快速切换，您不会想要这个提示）。我目前还没有讲vimrc，如果您没有vimrc配置文件，那就创建一个。它通常位于根目录下，名字叫.vimrc。我的vimrc位于~/.vimrc。要查看您自己的vimrc文件应该放置在哪，可以在Vim命令模式中输入:h vimrc。在vimrc文件中，添加：
set hidden

保存好vimrc文件，然后激活它(在vimrc文件中运行:source %)。


## buffers
buffer到底是什么？

buffer就是内存中的一块空间，您可以在这里写入或编辑文本。当您在Vim中打开一个文件时，文件的数据就与一个buffer绑定。当您在Vim中打开3个文件，您就有3个buffers。


vim file1.js file2.js

Vim当前显示的是file1.js的buffer，但它实际上创建了两个buffers：file1.jsbuffer和file2.jsbuffer。运行:buffers命令可以查看所有的buffers（另外，您也可以使用:ls和:files命令）。您应该会 同时 看到列出来的file1.js和file2.js。运行vim file1 file2 file3 ... filen创建n个buffers。每一次您打开一个新文件，Vim就为这个文件创建一个新的buffer。

:bnext 切换至下一个buffer（:bprevious切换至前一个buffer）。
:buffer + 文件名。（按下<Tab>键Vim会自动补全文件名）。
:buffer + n, n是buffer的编号。比如，输入:buffer 2将使您切换到buffer #2。
按下Ctrl-O将跳转至跳转列表中旧的位置，对应的，按下Ctrl-I将跳转至跳转列表中新的位置。这并不是属于buffer的特有方法，但它可以用来在不同的buffers中跳转。我将在第5章详细讲述关于跳转的知识。
按下Ctrl-^跳转至先前编辑过的buffer。


一旦Vim创建了一个buffer，它将保留在您的buffers列表中。若想删除它，您可以输入:bdelete。这条命令也可以接收一个buffer编号（:bdelete 3将删除buffer #3）或一个文件名（:bdelete然后按<Tab>自动补全文件名）。

我学习buffer时最困难的事情就是理解buffer如何工作，因为我当时的思维已经习惯了使用主流文本编辑器时关于窗口的概念。要理解buffer，可以打个很好的比方，就是打牌的桌面。如果您有2个buffers，就像您有一叠牌（2张）。您只能看见顶部的牌，虽然您知道在它下面还有其他的牌。如果您看见file1.jsbuffer，那么file1.js就是顶部的牌。虽然您看不到其他的牌file2.js，但它实际上就在那。如果您切换buffers到file2.js，那么file2.js这张牌就换到了顶部，而file1.js就换到了底部。

退出vim
:qall
:qall!

nvin
:qa!

保存并退出
:wqall!

## windows
一个window就是在buffer上的一个视口。如果您使用过主流的编辑器，Windows这个概念应该很熟悉。大部分文本编辑器具有显示多个窗口的能力。在Vim中，您同样可以拥有多个窗口。

vim file1.js
先前我说过，您看到的是file1.js的buffer。但这个说法并不完整，现在这句话得更正一下，您看到的是file1.js 的buffer通过 一个窗口 显示出来。窗口就是您查看的buffer所使用的视口。

先不忙急着退出Vim，在Vim中运行：

:split file2.js
现在您看到的是两个buffers通过 两个窗口 显示出来。上面的窗口显示的是file2.js的buffer。而下面的窗口显示的是file1.js的buffer。

如果您想在窗口之间导航，使用这些快捷键：

Ctrl-W H    移动光标到左边的窗口
Ctrl-W J    移动光标到下面的窗口
Ctrl-W K    移动光标到上面的窗口
Ctrl-W L    移动光标到右边的窗口


您可以使多个窗口显示同一个buffer。当光标位于左上方窗口时，输入：

:buffer file2.js

现在两个窗口显示的都是file2.js的buffer。如果您现在在这两个窗口中的某一个输入内容，您会看到所有显示file2.jsbuffer的窗口都在实时更新。

Ctrl-W V    打开一个新的垂直分割的窗口
Ctrl-W S    打开一个新的水平分割的窗口
Ctrl-W C    关闭一个窗口
Ctrl-W O    除了当前窗口，关闭所有其他的窗口

要关闭当前的窗口，您可以按Ctrl-W C或输入:quit。当您关闭一个窗口后，buffers仍然会在列表中。（可以运行:buffers来确认这一点）。

另外，下面的列表列出了一些有用的关于windows的命令行命令

:vsplit filename    垂直分割当前窗口，并在新窗口中打开名为filename的文件。
:split filename     水平分割当前窗口，并在新窗口中打开名为filename的文件。
:new filename       创建一个新窗口并打开名为filename的文件。

花一点时间理解上面的知识。要了解更多信息，可以查看帮助:h window。

花一点时间理解上面的知识。要了解更多信息，可以查看帮助:h window。

dd：删除当前行。
yy：复制当前行。
p：粘贴已复制或删除的文本。
u：撤销上一次操作。
Ctrl-r：重做上一次操作。
r：替换当前光标所在位置的字符。
c：删除从当前光标位置到指定位置的文本并进入插入模式。
v：进入可视模式，选择文本。
:s/<old>/<new>/g：将当前行中的<old>替换为<new>。
:%s/<old>/<new>/g：将整个文件中的<old>替换为<new>。


:sp：水平分屏当前窗口。
:vsp：垂直分屏当前窗口。
Ctrl-w h：将光标移到左侧窗口。
Ctrl-w j：将光标移到下方窗口。
Ctrl-w k：将光标移到上方窗口。
Ctrl-w l：将光标移到右侧窗口。
Ctrl-w +：增加当前窗口的高度。
Ctrl-w -：减小当前窗口的高度。

多文件编辑命令
在Vim中，您可以编辑多个文件。以下是一些多文件编辑命令：

:e <filename>：打开指定的文件。
:tabnew <filename>：在新选项卡中打开指定的文件。
:tabnext：切换到下一个选项卡。
:tabprev：切换到上一个选项卡。
:tabclose：关闭当前选项卡。


光标移动命令
在编辑文本时，移动光标是一个常见的操作。以下是一些常用的光标移动命令：

h：将光标向左移动一个字符。
j：将光标向下移动一行。
k：将光标向上移动一行。
l：将光标向右移动一个字符。
w：将光标移动到下一个单词的开头。
e：将光标移动到当前单词的末尾。
b：将光标移动到上一个单词的开头。
0：将光标移动到当前行的开头。
$：将光标移动到当前行的末尾。
G：将光标移动到文件的末尾。
gg：将光标移动到文件的开头。
/<pattern>：向下搜索<pattern>。

以下是一些基本的Vim命令：

i：在当前光标位置插入文本。
x：删除当前光标所在位置的字符。
:w：保存文件。
:q：退出Vim编辑器。
:q!：强制退出Vim编辑器，不保存文件。
:wq：保存文件并退出Vim编辑器。


一、移动光标
h,j,k,l 上，下，左，右
ctrl-e 移动页面
ctrl-f 上翻一页
ctrl-b 下翻一页
ctrl-u 上翻半页
ctrl-d 下翻半页
w 跳到下一个字首，按标点或单词分割
W 跳到下一个字首，长跳，如end-of-line被认为是一个字
e 跳到下一个字尾
E 跳到下一个字尾，长跳
b 跳到上一个字
B 跳到上一个字，长跳
0 跳至行首，不管有无缩进，就是跳到第0个字符
^ 跳至行首的第一个字符
$ 跳至行尾
gg 跳至文首
G 调至文尾
5gg/5G 调至第5行
gd 跳至当前光标所在的变量的声明处
fx 在当前行中找x字符，找到了就跳转至
; 重复上一个f命令，而不用重复的输入fx
* 查找光标所在处的单词，向下查找
# 查找光标所在处的单词，向上查找
二、删除复制
dd 删除光标所在行
dw 删除一个字(word)
d/D删除到行末x删除当前字符X删除前一个字符yy复制一行yw复制一个字y/D删除到行末x删除当前字符X删除前一个字符yy复制一行yw复制一个字y/Y 复制到行末
p 粘贴粘贴板的内容到当前行的下面
P 粘贴粘贴板的内容到当前行的上面
三、插入模式
i 从当前光标处进入插入模式
I 进入插入模式，并置光标于行首
a 追加模式，置光标于当前光标之后
A 追加模式，置光标于行末
o 在当前行之下新加一行，并进入插入模式
O 在当前行之上新加一行，并进入插入模式
Esc 退出插入模式
四、编辑
J 将下一行和当前行连接为一行
cc 删除当前行并进入编辑模式
cw 删除当前字，并进入编辑模式
c$ 擦除从当前位置至行末的内容，并进入编辑模式
s 删除当前字符并进入编辑模式
S 删除光标所在行并进入编辑模式
xp 交换当前字符和下一个字符
u 撤销
ctrl+r 重做
~ 切换大小写，当前字符
>> 将当前行右移一个单位
<< 将当前行左移一个单位(一个tab符)
== 自动缩进当前行
五、查找替换
/pattern 向后搜索字符串pattern
?pattern 向前搜索字符串pattern
"\c" 忽略大小写
"\C" 大小写敏感
n 下一个匹配(如果是/搜索，则是向下的下一个，?搜索则是向上的下一个)
N 上一个匹配(同上)
:%s/old/new/g 搜索整个文件，将所有的old替换为new
:%s/old/new/gc 搜索整个文件，将所有的old替换为new，每次都要你确认是否替换
六、退出编辑器
:w 将缓冲区写入文件，即保存修改
:wq 保存修改并退出
:x 保存修改并退出
:q 退出，如果对缓冲区进行过修改，则会提示
:q! 强制退出，放弃修改
七、多文件编辑
vim file1.. 同时打开多个文件
:args 显示当前编辑文件
:next 切换到下个文件
:prev 切换到前个文件
:next！ 不保存当前编辑文件并切换到下个文件
:prev！ 不保存当前编辑文件并切换到上个文件
:wnext 保存当前编辑文件并切换到下个文件
:wprev 保存当前编辑文件并切换到上个文件
:first 定位首文件
:last 定位尾文件
ctrl+^ 快速在最近打开的两个文件间切换
:split[sp] 把当前文件水平分割
:split file 把当前窗口水平分割, file
:vsplit[vsp] file 把当前窗口垂直分割, file
:new file 同split file
:close 关闭当前窗口
:only 只显示当前窗口, 关闭所有其他的窗口
:all 打开所有的窗口
:vertical all 打开所有的窗口, 垂直打开
:qall 对所有窗口执行：q操作
:qall! 对所有窗口执行：q!操作
:wall 对所有窗口执行：w操作
:wqall 对所有窗口执行：wq操作
ctrl-w h 跳转到左边的窗口
ctrl-w j 跳转到下面的窗口
ctrl-w k 跳转到上面的窗口
ctrl-w l 跳转到右边的窗口
ctrl-w t 跳转到最顶上的窗口
ctrl-w b 跳转到最底下的窗口
八、多标签编辑
:tabedit file 在新标签中打开文件file
:tab split file 在新标签中打开文件file
:tabp 切换到前一个标签
:tabn 切换到后一个标签
:tabc 关闭当前标签
:tabo 关闭其他标签
gt 到下一个tab
gT 到上一个tab
0gt 跳到第一个tab
5gt 跳到第五个tab
九、执行shell命令
1、在命令模式下输入":sh"，可以运行相当于在字符模式下，到输入结束想回到VIM编辑器中用exit，ctrl+D返回VIM编辑器
2、可以"!command"，运行结束后自动回到VIM编辑器中
3、用“Ctrl+Z“回到shell，用fg返回编辑
4、:!make -> 直接在当前目录下运行make指令
十、VIM启动项
-o[n] 以水平分屏的方式打开多个文件
-O[n] 以垂直分屏的方式打开多个文件
十一、自动排版
在粘贴了一些代码之后，vim变得比较乱，只要执行gg=G就能搞定
十二、如何在vim中编译程序
在vim中可以完成make,而且可以将编译的结果也显示在vim里，先执行 :copen 命令，将结果输出的窗口打开，然后执行 :make
编译后的结果就显示在了copen打开的小窗口里了，而且用鼠标双击错误信息，就会跳转到发生错误的行。
十三、buffer操作
1、buffer状态
- （非活动的缓冲区）
a （当前被激活缓冲区）
h （隐藏的缓冲区）
% （当前的缓冲区）
# （交换缓冲区）
= （只读缓冲区）
+ （已经更改的缓冲区）
十四、 VIM 操作目录
1.打开目录
vim .
vim a-path/
2.以下操作在操作目录时生效
p,P,t,u,U,x,v,o,r,s
c 使当前打开的目录成为当前目录
d 创建目录
% 创建文件
D 删除文件/目录
- 转到上层目录
gb 转到上一个 bookmarked directory
i 改变目录文件列表方式
^l 刷新当前打开的目录
mf - 标记文件
mu - unmark all marked files
mz - Compress/decompress marked files
gh 显示/不显示隐藏文件( dot-files)
^h 编辑隐藏文件列表
a 转换显示模式, all - hide - unhide
qf diplay infomation about file
qb list the bookmarked directories and directory traversal history
gi Display information on file
mb
mc
md - 将标记的文件(mf标记文件)使用 diff 模式
me - 编辑标记的文件,只显示一个，其余放入 buffer 中
mh
mm - move marked files to marked-file target directory
mc - copy
mp
mr
mt
vim 中复制,移动文件
1, mt - 移动到的目录
2, mf - 标记要移动的文件
3, mc - 移动/复制
R 移动文件
打开当前编辑文件的目录
:Explore
:Hexplore
:Nexplore
:Pexplore
:Sexplore
:Texplore
:Vexplore

