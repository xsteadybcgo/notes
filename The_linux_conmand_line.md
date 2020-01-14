# 《The Linux Command Line》学习笔记

> 系统化查缺补漏，记一些之前未使用到的命令

标点符号仅限 使用“.”，“-”，空格使用下划线“_”

- `ls -a` 现实所有文件（包含隐藏文件）
- `ls /usr` 直接列出usr目录
- `ls -lt -r` 长列表信息 按修改时间排序 再倒序 
- 可以串多个参数
- drwxr:第2-4位表示这个文件的属主拥有的权限，r是读，w是写，x是执行。

d | 第一位表示文件类型。d是目录文件，l是链接文件，-是普通文件，p是管道
:--- | :---
rwx | 第2-4位表示这个文件的属主拥有的权限，r是读，w是写，x是执行。
r-x | 第5-7位表示和这个文件属主所在同一个组的用户所具有的权限。
r-x | 第8-10位表示其他用户所具有的权限。

file 列出文件类型

`less`来查阅文本文件 `space`和`b`来改变翻页情况

/etc | 配置文件
:--- | :---
/usr | 包含用户所有文件与程序
/tmp | 存储临时文件的地方

在匹配文件的时候可以使用类似正则的匹配模式

- *.html 所有html文件
- [:lower:].html 以小写字母开头的文件，类似的还有[:alnum:] [:alpha:] [:digit:] [:lower:] [:upper:]

mkdir mv 等可以一次操作多个文件，如：
- mkdir dir1 dir2 dir3 创建多个文件夹
- mv file1 file2 dir 将多个文件移动到dir文件夹下

### `cp`
> **注意** 命令参数使用`cp -v a.js b.js` -v在cp后 而不是末尾

-r 递归复制
-u 仅复制目标目录中不存在的文件，或者是文件内容新于目标目录中已经存在的文件


### `rm`

  消息**删除**命令使用，`rm * .html`中间的空格会坑爹的把所有文件删除 并且可能告诉你找不到 .html 文件。
  
### `ln`

硬链接的局限性：
1. 一个硬链接不能关联它所在文件系统之外的文件。
2. 一个硬链接不能关联一个目录。

- 创建硬链接 `ln file link`
- 创建软链接 `ln -s item link`

链接就是创建文件额外的名字部分

```
ls -li 第一列为文件索引，可判断为同一文件

26070994 drwxr-xr-x  3 xiangwen  staff    96  1 13 21:55 dir1
26070995 drwxr-xr-x  3 xiangwen  staff    96  1 13 21:55 dir2
26071184 -rw-r--r--  4 xiangwen  staff  6804  1 13 21:48 fun
26071184 -rw-r--r--  4 xiangwen  staff  6804  1 13 21:48 fun-hard
```

`zless`可用以查看gzip压缩的文件

清空文件的技巧 `> xxx文件`
增量重定向文件 `/usr/bin >> ls-output.txt` 使用`>>`双大于号
错误文件重定向 `/usr/bin 2> ls-output.txt` 1标准输出 2标准输出


### `cat`
`cat stdin > stdout` 连接文件，注意省略写法

### 管道 `|`
一个命令的标准输出可以通过管道送至另一个命令的标准输入:
`ls -l /usr/bin | less`, 
合并排序输出： `ls /bin /usr/bin | sort | uniq [-d]| less` 其中`-d`输出显示重复的结果，将`less`替换为`wc -l`统计数据

`grep`匹配模式 `head/tail` 前后行数 默认10行 `-n`控制行数

`tee` 管道专用输入输出流

`$((exp))` `ls -A`列出包含隐藏文件



