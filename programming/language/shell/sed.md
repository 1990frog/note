[TOC]

# 概览
sed(stream editor)，流编辑器。对标准输出或文件逐行进行处理

# 语法
stdout | sed [option] "pattern command"
sed [option] "pattern command" file

# sed选项（option）
选项 | 含义
-----|--------------------------------------------
-n   | 只打印模式匹配行，不打印原始行
-e   | 直接在命令行进行sed编辑，默认选项
-f   | 编辑动作保存在文件中，指定文件执行。"pattern command" 存储在文件中。
-r   | 支持扩展正则表达式
-i   | 直接修改文件内容

## -n
仅匹配打印内容
```

```

sed 'p' xxx
本身打印一遍，p命令又打印一遍，输出两遍
不加-n原行信息也打印

sed -n '/python/p' xxx
正则包含python的行，打印

sed -n -e '/python/p' -e '/PYTHON/p' xxx



sed -n -r '/python|PYTHON/p' xxx

-f
vim function.sed
/python/p

sed -n -f function.sed xxx

sed -n 's/love/like/g' xxx

sed -n 's/love/like/g;p' xxx

sed -i 's/love/like/g' xxx
源文件修改


-n 不支持扩展正则表达式，使用-r


替换字符串
's/{被替换字符串}/{替换成的字符串}/g'


```
➜  shell cat test.md
PYTHON
PyTHon
python
➜  shell sed -n 's/python/java/g' test.md
➜  shell sed -n 's/python/java/g;p' test.md
PYTHON
PyTHon
java
➜  shell sed -i 's/python/java/g' test.md
➜  shell cat test.md
PYTHON
PyTHon
java
➜  shell
```