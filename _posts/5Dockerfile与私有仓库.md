##### 创建目录
```
mkdir -p /usr/local/dockerjdk8
```
##### 下载jdk-8u171-linux-x64.tar.gz并上传到服务器（虚拟机）中的/usr/local/dockerjdk8目录
```
vi Dockerfile
```
```
#依赖镜像名称和ID
FROM centos:7
#指定镜像创建者信息
MAINTAINER ITCAST
#切换工作目录
WORKDIR /usr
RUN mkdir  /usr/local/java
#ADD 是相对路径jar,把java添加到容器中
ADD jdk-8u171-linux-x64.tar.gz /usr/local/java/

#配置java环境变量
ENV JAVA_HOME /usr/local/java/jdk1.8.0_171
ENV JRE_HOME $JAVA_HOME/jre
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib:$CLASSPATH
ENV PATH $JAVA_HOME/bin:$PATH
```
##### 执行命令构造镜像
```
docker build -t='jdk1.8' .
```

### Docker私有仓库
###### 拉取镜像
```
docker pull registry
```
```
docker run -di --name=registry -p 5000:5000 registry
```
###### 访问浏览器
```
http://106.12.207.31:5000/v2/_catalog
```
结果:{"repositories":[]},表示仓库搭建成功且内容为空
###### 修改daemon.json
```
vi /etc/docker/daemon.json
```
###### 添加内容,保存退出
```json
{"insecure-registries":["106.12.207.31:5000"]} 
```
让docker信任私有仓库地址
###### 重启docker服务
```
systemctl restart docker
```
#### 镜像上传私有仓库
```
docker tag jdk1.8 106.12.207.31:5000/jdk1.8
docker start registry
docker push 106.12.207.31:5000/jdk1.8
```