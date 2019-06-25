### mount命令详解

#### 具体的使用命令格式如下所示：
> mount [-t vfstype] [-o options] device dir

其中，具体的解释如下：

1. -t vfstype指定文件系统的类型，通常不需要指定，mount会自动选择正确的类型。
2. -o options主要用来描述设备或者档案的挂接方式，常用的参数有：
    - loop：用来把一个文件当成硬盘分区挂接上系统
    - ro：采用只读方式挂接设备
    - rw：采用读写方式挂接设备
    - iocharest：指定访问文件系统所用的字符集
3. device 需要挂接的设备
4. dir 设备在系统上的挂节点

### unmount命令

```
unmount device
unmount mount_point
```
#### fuser 

- fuser查看正在访问指定文件系统的进程
  > fuser -v mount_point
- 终止所有正在访问指定文件系统的进程：慎用
  > fuser -km mount_point


### sshfs挂载命令使用

在服务器上经常要直接操作另一台服务器的某一些资源文件的情况，例如一台程序服务器，一台资源服务器，程序服务器可以直接挂载资源服务器的某一个目录，然后直接上传文件到资源服务器了。

#### 安装sshfs
> yum -y install fuse-sshfs

安装完成后，系统会自动建立fuse用户组，要使用sshfs的用户只要加入这个用户即可。

#### 挂载远程目录

> sshfs user@iphost:path mout_point

> eg：sshfs root@127.0. 0. 0:/data/www/rabbit/Upload/ /mnt/file_server_storage

#### 卸载挂载点

当不需要的时候，可以使用fusermount命令来卸载
> fusermount -u mount_point

一些基本的操作命令：
- -h :print help.
- -V:print version.
- -o:OPTION[,OPTION...] mount options.
- -u:unmount.
- -q:quiet.
- -z:lazy unmount.

