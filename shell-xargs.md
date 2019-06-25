### Linux xargs命令

#### 主要作用

1. xargs是给命令传递参数的一个过滤器，也是组合多个命令的一个工具
2. xargs可以将管道或标准输入（stdin）数据转换成命令行参数，也能够从文件的输出中读取数据
3. xargs可以将单行或者多行文本输入转换为其他格式，如单行变多行、多行变单行
4. xargs默认命令是echo，即通过管道传递给xargs的输入会包含换行和空白，通过xargs命令的处理，换行和空白将被空格取代
5. xargs命令类似管道，可以捕获一个命令的输出，然后传递给另外一个命令
6. 之所以会用到，是很多命令不支持 | 管道传递参数，所以xargs一般和 | 命令一起使用

#### Example

```
#基本的格式
command | xargs -item command
```
一些基本的指令
1. -a file 表示从文件中读入作为sdtin
2. -e flag 有时候可能是-E，flag必须是一个以空格分隔的标志，当xargs分析到这个标志的时候就会停止
3. -p 当每次执行一个argument的时候询问一次用户
4. -n num 后面加上次数，表示命令在执行的时候一次用的argument的个数，默认是所有的
5. -t 表示先打印命令，然后在执行
6. -P 修改的最大进程数，默认是1，大多数的时候用不到该命令
7. -d 分隔符，默认的xargs分隔符是回车，argument的分隔符是空格，这里修改的是分隔符