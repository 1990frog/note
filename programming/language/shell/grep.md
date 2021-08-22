[TOC]

# grep
+ grep [option] [pattern] [file1,fiel2,...]
+ command | grep [option] [pattern]

选项    含义
-v      不显示匹配行信息
-i      忽略大小写
-n      显示行号
-r      递归搜索
-E      支持扩展正则
-F      不按正则表达式匹配，按照字符串字面意思匹配
-c      只显示匹配行数
-w      匹配整词
-x      匹配整行
-l      只显示文件名，不显示内容
-s      不显示错误信息


grep和egrep
grep默认不支持拓展正则，需要加-E