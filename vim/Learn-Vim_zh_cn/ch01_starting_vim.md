[TOC]

# 第1章 起步 

在本章，您将了解从终端启动Vim的几种不同方法。我写这本教程时使用的Vim版本是8.2。如果您使用Neovim或老版本的Vim，大部分情况下方法是通用的，但注意个别命令可能无效。

## 安装

我不会给出在某台特定机器上安装Vim的详细指令。好消息是，大部分Unix-based电脑应该预装了Vim。如果没有，大部分发行版也应该有关于如何安装Vim的指令。

从Vim的官方网站或官方仓库可以获得下载链接：
- [Vim 官网](https://www.vim.org/download.php)
- [Vim 官方仓库](https://github.com/vim/vim)
- [Vim 官方仓库镜像](https://hub.fastgit.org/vim/vim)

## Vim命令

当您安装好Vim后，在终端运行以下命令：

```bash
vim
```

您应该会看到一个介绍界面。这就是您用来处理文本的工作区。不像其它大部分文本编辑器和IDE，Vim是一个模式编辑器。如果您想输入"hello"，您需要使用'i'命令切换到插入模式。按下'ihello<Esc>'可以在工作区插入文本"hello"。

## 退出Vim

有好几种不同的方法都可以退出Vim。（译者注：在stackflow论坛上，有个著名的问题“如何退出Vim”，五年来，有超过100万开发者遇到相同的问题。^_^，这件事已经成为了开发者中的一个梗）。最常用的退出方法是在Vim中输入：

```
:quit
```

您可以使用简写`:q`。这是一个命令行模式的命令(command-line mode：Vim的另一种模式)。如果您在普通模式输入`:`，光标将移动到屏幕底部，在这里您可以输入命令。在后面的第15章，您会学到关于命令行模式更多信息。如果您处于插入模式，按下`:`将会在屏幕上直接显示":"(冒号)。因此，您需要按下`<Esc>`键切换回普通模式。顺带说一下，在命令行模式也可以通过按`<Esc>`键切换回普通模式。您将会注意到，在Vim的好几种模式下都可以通过按`<Esc>`键切回普通模式。

## 保存文件

若要保存您的修改，在Vim中输入：

```
:write
```

您也可以输入简写':w'。如果这是一个新建的文件，您必须给出文件名才能保存。下面的命令使文件保存为名为'file.txt'的文件，在Vim命令行运行：

```
:w file.txt
```

如果想保存并退出，可以将':w'和':q'命令联起来，在Vim命令行中输入：

```
:wq
```

如果想不保存修改而强制退出，可以在':q'命令后加'!'（叹号）,在Vim命令行中：

```
:q!
```

## 帮助

在本指南全文中，我将向您提及好几种Vim的帮助页面。您可以通过输入`:help {命令}`(`:h`是简写)进入相关命令的帮助文档。可以向`:h`命令传递主题、命令名作为参数。比如，如果想查询退出Vim的方法，在vim中输入：

```
:h write-quit
```

我是怎么知道应该搜索"write-quit"这个关键词的呢？实际上我也不知道，我仅仅只是输入':h quit'，然后按`<Tab>`。Vim会自动显示相关联的关键词供用户选择。如果您需要查询一些信息，只需要输入`:h`后接关键词，然后按`<Tab>`。

## 打开文件

如果想在终端中使用Vim打开名为('hello1.txt')，在终端中运行：

```bash
vim hello1.txt
```

可以一次打开多个文件，在终端中：

```bash
vim hello1.txt hello2.txt hello3.txt
```

Vim会在不同的buffers中打开'hello1.txt'，'hello2.txt'，'hello3.txt'。在下一章您将学到关于buffers的知识。

## 参数

您可以在终端中向`vim`命令传递参数。  

如果想查看Vim的当前版本，在终端中运行：

```bash
vim --version
```

终端中将显示您当前Vim的版本和所有支持的特性，'+'表示支持的特性，'-'表示不支持的特性。本教程中的一些操作需要您的Vim支持特定的特性。比如，在后面的章节中提到可以使用`:history`查看Vim的命令行历史记录。您的Vim必须包含`+cmdline_history`这一特性，这条命令才能正常使用。一般情况下，如果您通过主流的安装源下载Vim的话，您安装的Vim是支持所有特性的，

您在终端里做的很多事情都可以在Vim内部实现。比如，在Vim程序中也可以查看当前Vim版本，您可以运行下面的命令，在Vim中输入：

```
:version
```

如果您想打开`hello.txt`文件后迅速执行一条命令，您可以向`vim`传递一个`+{cmd}`选项。

在Vim中，您可以使用`:s`命令（`substitue`的缩写）替换文本。如果您想打开`hello.txt`后立即将所有的"pancake"替换成"bagel"，在终端中：

```bash
vim +%s/pancake/bagel/g hello.txt
```

该命令可以被叠加，在终端中：

```bash
vim +%s/pancake/bagel/g +%s/bagel/egg/g +%s/egg/donut/g hello.txt
```

Vim会将所有"pancake" 实例替换为"bagel"，然后将所有"bagel"替换为"egg"，然后将所有"egg"替换为"donut"（在后面的章节中您将学到如何替换）。

您同样可以使用`c`标志来代替`+`语法，在终端中：

```bash
vim -c %s/pancake/bagel/g hello.txt
vim -c %s/pancake/bagel/g -c %s/bagel/egg/g -c %s/egg/donut/g hello.txt
```

## 打开多个窗口

您可以使用`o`和`O`选项使Vim打开后分别显示为水平或垂直分割的窗口。

若想将Vim打开为2个水平分割的窗口，在终端中运行：
```bash
vim -o2
```

若想将Vim打开为5个水平分割的窗口，在终端中运行：
```bash
vim -o5
```

若想将Vim打开为5个水平分割的窗口，并使前两个窗口显示`hello1.txt`和`hello2.txt`的内容，在终端中运行：

```bash
vim -o5 hello1.txt hello2.txt
```

若想将Vim打开为2个垂直分割的窗口、5个垂直分割的窗口、5个垂直分割窗口并显示2个文件，在终端中分别运行以下命令：

```bash
vim -O2
vim -O5
vim -O5 hello1.txt hello2.txt
```

## 挂起

如果您编辑时想将Vim挂起，您可以按下`Ctrl-z`。同样，您也可以使用`:stop`或`:suspend`命令达到相同的效果。若想从挂起状态返回，在终端中运行`fg`命令。

## 聪明的启动Vim

您可以向`vim`命令传递不同的选项(option)和标志(flag)，就像其他终端命令一样。其中一个选项是命令行命令（`+{cmd}`或`-c cmd`）。当您读完本教程学到更多命令后，看看您是否能将相应命令应用到Vim的启动中。同样，作为一个终端命令，您可以将`vim`命令和其他终端命令联合起来。比如，您可以将`ls`命令的输出重定向到Vim中编辑，命令是`ls -l | vim -`。

若要了解更多Vim终端命令，查看`man vim`。若要了解更多关于Vim编辑器的知识，继续阅读本教程，多使用`:help`命令。

## 链接
- [目录](./directory.md)
- 上一部分 [Ch 0 - 请先阅读](./ch00_read_this_first.md)
- 下一部分 [Ch 2 - 缓冲区，窗口和选项卡](./ch02_buffers_windows_tabs.md)