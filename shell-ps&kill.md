## linux命令之ps

ps命令是Process Status的缩写，ps命令用于列出系统当前正在运行的进程快照，就是执行ps命令时刻时运行的进程，动态的显示进程信息使用top或者是htop命令。该命令可以查看到哪些进程正在运行和运行的状态、进程是否结束、进程是否僵死、哪些进程占用了过多的资源等。总之大部分的信息都可以通过该命令得到。
### linux进程的五种状态
1. 运行 （正在运行或者运行队列中等待）
2. 中断 （休眠、受阻、在等待某个条件的形成或接受到信号）
3. 不可中断 （收到信号不唤醒和不可运行，进程必须等待直到）
4. 僵死 （进程已经终止，但是进程的描述符还在，知道父进程调用wati4()系统调用后释放）
5. 停止（进程收到SIGSTOP、SIGSTP、SIGTIN、SIGTOUD等信号后停止运行）

### ps工具标示的五种状态码

1. D 不可中断（uninterruptible sleep (usually IO Process)）
2. R 运行 runnable (on run quene)
3. S 中断 sleeping
4. T 停止 traced os stopped
5. Z 僵死 a defunct （zombie）process

### ps的命令基本操作

- 命令格式
  `ps [options]`
- 命令功能
  
  用来显示当前进程的状态

- 命令参数

    a 显示所有的进程

    -a 显示同一终端下的所有程序

    -A 显示所有的进程

    c 显示进程的真实名称

    -N 反向选择

    -e 等同与-A

    f 显示程序间的关系

    r 显示当前终端的进程

    T 显示当前终端的所有程序

    u 指定用户的所有进程

    -au 显示比较详细的资讯

    -aux 显示所有包含其他使用者的进程

    -C 'command' 列出指定命令的状态

    --lines '字符数' 每页显示的字符数

    --version 显示版本信息

## kill命令

linux中的kill命令是用来终止指定进程的运行，是比较常用的一个命令，通常，终止一个前台运行的进程可以使用ctrl+c的命令，对于后台执行的进程而言，必须要使用kill命令来终止。首先需要使用top、ps、pidof等命令来获取进程的pid，然后使用kill命令终止掉。【默认情况下，采用编号为15的TERM信号，TERM信号将终止所有不能捕获该信号的进程，对于那些可以捕获信号的进程就要采用编号为9的kill信号，强行终止该进程】

### kill命令的基本操作

- 命令格式
    
    kill [参数] [进程号]

- 命令功能

    发送指定的信号到相应进程，不指定型号将发送SIGTERM信号（15）终止指定进程。如果任无法终止该程序可以使用-KILL参数，其发送的信号为SIGTERM(9),将强制结束进程，使用ps命令或者jobs命令可以查看进程号，root用户将影响用户的进程，非root用户只能影响自己的进程。

- 命令参数

    -l 信号，如果不加信号的编号参数，则使用-l参数会列出全部的信号名称

    -a 当处理当前进程时，不限制命令名和进程号的对应关系

    -p 指定kill命令只打印相关进程的进程号，而不发送任何信号

    -s 指定发送信号

    -u 指定用户

    ***注意***

    1. kill命令可以带信号号码选项，也可以不带，如果没有信号号码，kill命令就会发出终止信号，这个信号可以被进程捕获，使得进程在退出之前可以清理并释放资源，也可以用kill信号向进程发送指定的信号。例如kill  -2 123
    2. kill可以代用进程ID号作为参数，如果对当前进程没有权限，就会得到一个错误信号
    3. 可以同时向多个进程发送信号
    4. 当kill发送信号成功后，shell会显示出进程终止的信息。
    5. 使用kill命令时，一定要多加小心。

- 使用实例

    常用的进程信号使用

    HUP 1  终端断线

    INT 2 中断 （同ctrl+c）

    QUIT 3 退出，同ctrl + \

    TERM 15 终止

    KILL 9 强制终止

    CONT 18 继续 

    STOP 19 暂停 同ctrl + z

  例如：`kill -9 pid` 最常用的信号