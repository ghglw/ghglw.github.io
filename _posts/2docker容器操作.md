### 容器命令
###### 查看正在运行的容器
```
docker ps
```
###### 查看所有容器
```
docker ps -a
```
###### 查看最后一次运行的容器
```
docker ps -l
```
###### 查看停止的容器
```
docker ps -f status=exited
```
### 创建容器
###### 交互式创建容器
```
docker run -it --name=容器名称 镜像名称:标签 /bin/bash
```
```
exit //退出当前容器
```
###### 守护式创建,登陆容器
```
docker run -di --name=容器名称 镜像名称:标签
```
```
docker exec -it 容器名称或ID /bin/bash
```
### 容器启停
```
docker stop 容器名称或ID
```
```
docker start 容器名称或ID
```
###### 文件拷贝
```
docker cp source 容器名称:容器目录
docker cp 容器名称:容器目录源 拷贝路径
```
###### 目录挂载
```
docker run -di -v /usr/local/myhtml:/usr/local/myhtml --name=mycentos3 centos:7
```
添加参数 --privileged=true 来解决挂载的目录没有权限的问题
###### 查看容器ip
```
docker inspect 容器名称或ID
```
###### 删除容器
```
docker rm 容器名称或ID
```