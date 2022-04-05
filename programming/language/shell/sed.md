[TOC]

# 概览
sed(stream editor)，流编辑器。对标准输出或文件逐行进行处理

# 语法
stdout | sed [option] "pattern command"
sed [option] "pattern command" file
```
用法: sed [选项]... {脚本(如果没有其他脚本)} [输入文件]...

  -n, --quiet, --silent
                 取消自动打印模式空间
      --debug
                 对程序运行进行标注
  -e 脚本, --expression=脚本
                 添加“脚本”到程序的运行列表
  -f 脚本文件, --file=脚本文件
                 添加“脚本文件”到程序的运行列表
  --follow-symlinks
                 直接修改文件时跟随软链接
  -i[扩展名], --in-place[=扩展名]
                 直接修改文件（如果指定扩展名则备份文件）
  -l N, --line-length=N
                 指定“l”命令的换行期望长度
  --posix
                 关闭所有 GNU 扩展
  -E, -r, --regexp-extended
                 在脚本中使用扩展正则表达式
                 （为保证可移植性使用 POSIX -E）。
  -s, --separate
                 将输入文件视为各个独立的文件而不是单个
                 长的连续输入流。
      --sandbox
                 在沙盒模式中进行操作（禁用 e/r/w 命令）。
  -u, --unbuffered
                 从输入文件读取最少的数据，更频繁的刷新输出
  -z, --null-data
                 使用 NUL 字符分隔各行
      --help     打印帮助并退出
      --version  输出版本信息并退出

如果没有 -e, --expression, -f 或 --file 选项，那么第一个非选项参数被视为
sed脚本。其他非选项参数被视为输入文件，如果没有输入文件，那么程序将从标准
输入读取数据。
GNU sed 主页：<https://www.gnu.org/software/sed/>。
使用 GNU 软件的一般性帮助：<https://www.gnu.org/gethelp/>。
请将错误报告发送至：<bug-sed@gnu.org>。
```

# 参数（option）
选项 | 含义
-----|--------------------------------------------
-n   | 仅显示script处理后的结果，不打印原始行
-e   | 直接在命令行进行sed编辑，默认选项
-f   | 编辑动作保存在文件中，指定文件执行。"pattern command" 存储在文件中。
-r   | 支持扩展正则表达式
-i   | 直接修改文件内容

## -n
仅匹配打印内容
```shell
➜  shell ls
func.sed  sed.md
➜  shell cat sed.md
PYTHON
PyTHon
java
➜  shell sed -n 's/PYTHON/java/g;p' sed.md
java
PyTHon
java
➜  shell sed -n '/PYTHON/p' sed.md
PYTHON
➜  shell cat sed.md
PYTHON
PyTHon
java
➜  shell
```

## -e
-e<script>或--expression=<script> 以选项中指定的script来处理输入的文本文件
```shell
➜  shell cat sed.md
PYTHON
PyTHon
java
➜  shell sed -n -e'/PYTHON/p' -e'/java/p' sed.md
PYTHON
java
```

## -f
以选项中指定的script文件来处理输入的文本文件
```shell
➜  shell ls
func.sed  sed.md
➜  shell cat func.sed
/PYTHON/p
➜  shell sed -f func.sed sed.md
PYTHON
PYTHON
PyTHon
java
➜  shell sed -n -f func.sed sed.md
PYTHON
```

## -r
支持正则表达式
```shell
➜  shell cat sed.md
PYTHON
PyTHon
java
➜  shell sed -r '/PYTHON|PyTHon/p' sed.md
PYTHON
PYTHON
PyTHon
PyTHon
java
➜  shell sed -n -r '/PYTHON|PyTHon/p' sed.md
PYTHON
PyTHon
```

## -i
直接修改文件
```shell
➜  shell cat sed.md
PYTHON
PyTHon
java
➜  shell sed -i 's/java/python/g' sed.md
➜  shell cat sed.md
PYTHON
PyTHon
python
```

# 动作（script）
动作 | 含义
-----|-------------------------------------------------------
a    | 新增， a 的后面可以接字串，而这些字串会在新的一行出现(目前的下一行)
i    | 插入， i 的后面可以接字串，而这些字串会在新的一行出现(目前的上一行)
r    | 追加， r 将后面指定文件的内容追加到当前匹配行的后面(当前行)
w    | 将匹配到的行内容另存为其他文件中



c    | 取代， c 的后面可以接字串，这些字串可以取代 n1,n2 之间的行
d    | 删除，因为是删除啊，所以 d 后面通常不接任何东东

p    | 打印，亦即将某个选择的数据印出。通常 p 会与参数 sed -n 一起运行
s    | 取代，可以直接进行取代的工作哩！通常这个 s 的动作可以搭配正规表示法！例如 1,20s/old/new/g


查询
p打印

增加
a(append)行后追加
i(insert)行前追加
r(read)外部文件读入，行后追加
w(write)匹配行写入外部文件

删除
d(delete)删除

修改
s/old/new 将行内第一个old替换成new
s/old/new/g 将行内全部的old替换成new
s/old/new/2g 将行内前两个old替换成new
s/old/new/ig 将行内old全部替换为new，忽略大小写


sed [option] "/pattern/command" file
# pattern的用法

LineNumber  直接指定行号
sed -n "17p" file 
打印file文件的第17行

StartLine,EndLine 指定起始行号和结束行号
sed -n "10,20p" file

Starting,+N 指定起始行号，然后后面N行
sed -n "10,+5p" file

/pattern1/ 正则表达式匹配的行
sed -n "/^root/p" file

/pattern1/,/pattern2/ 正则表达式区间
sed -n "/^ftp/,/^mail/p" file

LineNumber,/pattern1/ 从指定行号开始匹配，直到匹配pattern1的行
sed -n "4,/^hdfs/p" file

/pattern1/,LineNumber
sed -n "/^hdfs/,4p" file



---

sed -i '/^hdfs/,/^yarn/i xxxxxx' xxxn

---

替换

s/old/new/ 查找并替换第一个
s/old/new/g 查找并替换全部
s/old/new/2 只替换第2个
s/old/new/2g 同第二个开始匹配，替换所有
s/old/new/ig 忽略大小写替换1全部

= 显示匹配数据的行号

sed -n '/root/cai/=' xxx


---

反向引用

sed -i 's/had..p/&s/g' xxx
sed -i 's/\(had..p\)/\1s/g' xxx