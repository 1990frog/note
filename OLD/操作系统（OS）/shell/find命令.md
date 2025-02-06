[TOC]

语法格式
find [路径] [选项] [操作]

选项 | 含义
---|---
-name | 根据文件名查找
-iname | 根据文件名查找，忽略大小写
-perm | 根据文件权限查找
-prune | 该选项可以排除某些查找目录
-user | 根据文件属主查找
-group | 根据文件用户组查找
-mtime | 根据文件更改时间查找
-nogroup | 查找无有效用户组的文件
-nouser | 查找无有效用户的文件
-newer file1 ! file2 | 查找更改时间比file1新但比file2旧的文件
-type | 按文件类型查找
-size | 按文件大小查找
-mindepth | 从n级子目录开始搜索
-maxdepth | 最多搜索到n级子目录


# find、locate、whereis、which
find在磁盘中查找，默认全部匹配
locate在数据库文件中查找，默认部分匹配
whereis查找某个命令的二进制程序文件、帮助文档、源代码文件
-b 只返回二进制文件
-m 只返回帮助文档文件
-s 只返回源代码文档
which仅查找二进制程序文件