## ssh命令

1. ssh -p port user@host
   > 使用上述命令可以登录服务器，-p表示端口号
2. ssh-copy-id -i ~/.ssh/sshkey.pub-p port user@host
   > 使用上述命令将自己本地的ssh-key文件拷贝到服务器中，使用这种方式之后，下次登录可以不用在输入密码。
3. ssh pi@10.42.0.47 ls -l
   > 在远程主机执行一条命令，将结果显示到本地 
4. ssh-keygen : 生成自己的公钥，这个只需要生成一次即可，保存在~/.ssh/目录下面。其中id_rsa.pub为公钥，id_rsa为私钥。

## scp命令

1. -1 强制scp命令使用ssh1协议
2. -2 强制scp命令使用ssh2
3. -B 使用批处理模式
4. -C 允许压缩
5. -p 保留源文件的修改时间、访问时间和访问权限
6. -q 不显示进度条
7. -r 递归复制整个目录
8. -v 详细方式显示输出
9. -P port 指定端口号

#### 基本的使用方式
- 本地复制远程文件：
  `scp root@www.test.com:/val/test/test.tar.gz /val/test/test.tar.gz`

- 远程复制本地文件：`scp /val/test.tar.gz root@www.test.com:/val/test.tar.gz`

- 本地复制远程目录：`scp -r root@www.test.com:/val/test/ /val/test/`

- 远程复制本地目录：`scp -r ./ubuntu_env/ root@192.168.0.111:/home/pipi`