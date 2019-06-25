## find命令的使用

find是一个功能强大并且经常使用的命令，所以一定要掌握。
使用方式：`find [path] [option] [action]`

### 与时间相关的参数

> - -mtime n :n为数字，意思是在n天之前的“一天内”被改过的文件
> - -mtime +n:列出在n天之前（不包含n天本身）更改过的文件
> - -mtime -n：列出在n天之内被更改过的文件
> - -newer file：列出比file还要新的文件名 
> - eg：`find ./ -mtime 0 # 查找今天改动的文件`

### 与用户或者用户组名有关的参数

> - -user name:列出文件所有者为name的文件
> - -group name：列出文件所属用户组为name的文件
> - -uid n：列出文件所有者为用户id为n的文件
> - -gid n：列出文件所属用户组为用户组id为n的文件
> - eg：`find ./ -user sholy #查找当前目录下文件所有者为sholy的文件`

### 与文件权限和名称或者大小相关参数

> - -name filename:文件名为filename的文件（常用）
> - -size [+-]size:找出比size大+或者小-的文件
> - -type Type:查找文件类型为type的文件，一般文件的类型包括一般文件（f）、设备文件（b、c）、目录（d）、连接文件（l）、socket（s）、FIFO管道文件（p）
> - -perm mode：查找文件权限刚好等于mode的文件，用数字表示，如0755，（+-）表示大于mode或者小于mode的文件

