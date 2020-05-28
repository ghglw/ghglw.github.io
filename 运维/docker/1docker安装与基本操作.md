### docker 安装
###### 更新yum
```
sudo yum update
```
###### 安装docker依赖软件
```
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
```
###### 修改yum源为阿里云
```
sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```
###### 安装docker
```
sudo yum install docker-ce
```
###### 检查docker版本
```
docker -v
```
###### 设置ustc的镜像
```
vi /etc/docker/daemon.json
```
添加内容
```
{ "registry-mirrors": ["https://docker.mirrors.ustc.edu.cn"] }
```

### docker基本操作
###### 启动docker
```
systemctl start docker
```
###### 停止docker
```
systemctl stop docker
```
###### 重启docker
```
systemctl restart docker
```
###### 查看docker状态
```
systemctl status docker
```
###### docker开机自启
```
systemctl enable docker
```
###### 概要信息与帮助文档
```
docker info
docker --help
```
### docker镜像相关操作
###### 查看镜像
```
docker images
```
###### 搜索镜像
```
docker search 镜像名称
```
###### 拉取镜像
```
docker pull 镜像名称
```
###### 删除镜像
```
docker rmi 镜像ID
```
