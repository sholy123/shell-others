## 容器数据卷

1. 做数据持久化
2. 希望多个容器之间共享数据，重用数据
3. 数据卷中的更改不会包含在镜像的更新中
4. 数据卷的声明周期一直持续到容器没有使用它位置

### 容器内添加持久卷的操作

1. 直接命令添加
   1. docker run -it -v /宿主机绝对目录：/容器内文件目录 镜像名 #这个宿主机的路径可以不存在，docker会自动建立
   2. 使用-v命令挂载之后，主机和容器之间通过共享文件夹共享数据，容器停止之后，持久卷中的数据也不会丢失。
   3. 挂载的目录权限是RW，并且权限是可修改的，容器内仅可以读。docker run -it -v /宿主机绝对目录：/容器内文件目录:ro 镜像名
   
2. Dockerfile中添加
   1. 指令：VOLUME ["/dataContainer1","/dataContainer2"]
   2. 查看容器中挂载本机的地址，使用inspect命令查看

#### 数据卷容器

1. 父容器为挂载数据的容器，其他的容器继承该容器，则该容器成为数据卷容器
2. 执行命令：docker run -it --name dc02 --volumes-from dc01 镜像名，所有的启动的容器都共享该目录，直到所有的容器都停止使用该目录


## Dockerfile

1. What：构建镜像的构建文件，由一系列命令构成的脚本
2. 构建过程从上到下依次构建，逐条指令对容器进行修改

docker run -it -v /home/appuser/sholy/docker-dis:/home  docker-registry.saicstack.com/ai-dlaas/python3-distortion:v6.6 bash 