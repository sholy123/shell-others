## nc 命令详解

nc命令是网络工具中的瑞士军刀，能够通过TCP和UDP在网络中读写数据。通过与其他工具的结合和定向，可以在脚本中以多种的方式使用它，具体的操作方式如下：

## 使用实例

#### 1. 端口扫描

端口扫描经常被系统管理源使用来法发现一些机器上开放的端口。

```shell
nc -z -v -n 172.31.100.7 21-25
```

可以运行在TCP或者UDP模式，默认是TCP，-u参数调整为UDP

- -z 参数表示使用0 IO，连接成功之后立即关闭连接，不进行数据交换
- -v 参数表示使用冗余选项，也就是详细输出
- -n 参数表示不使用DNS反向查询IP地址的域名

该命令会答应21-25所有开放的端口。banner是一个文本，是你连接的服务发送给你的文本信息。

```shell
nc -v 172.31.100.7 21
```

- 该命令会连接开放端口21并打印运行在这个端口上服务的banner信息。

#### 2. 聊天服务

#### 3. 文件传输

#### 4. 目录传输

#### 5. 加密发送数据



## linux上查看端口是否被占用

1. 示例1

   ```shell
   lsof -i:80
   ```

   - 上述命令表示检查80端口是否被占用，若被占用，则显示被占用的信息，否则的话没有显示。
   - 如果不加端口号的话，会显示所有的占用的端口。

2. 示例2

   ```shell
   netstat -anp | grep 80
   ```

   - 检查80端口是否被占用
   - 需要在sudo权限下操作。