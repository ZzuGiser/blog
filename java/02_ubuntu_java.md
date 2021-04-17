### UBUNTU 后端学习环境配置

#### 1 java 8 环境配置

```sh
# 安装openjdk
sudo apt-get update
sudo apt-get install openjdk-8-jdk
java -version

# 安装oracle Java JDK
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
java -version
```

#### 2 docker 安装

```bash
# 使用官方安装脚本自动安装
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
# 测试运行
sudo docker run hello-world

# 测试添加用户组
cat /etc/group | grep docker
sudo gpasswd -a ${USER} docker
newgrp - docker
sudo service docker restart
docker run hello-world

```

#### 3 docker 常用命令

``` bash
#镜像命令
$docker images -a:列出本地所有的镜像（含中间） -q:只显示镜像ID --digests： 显示镜像的摘要信息 
$docker search 镜像名  从官网搜索镜像
$docker pull 镜像名[:tag] 下载镜像 
$docker rmi -f 镜像ID 
$docker rmi -f $(docker images -qa)
$docker commit -m="描述信息" -a="作者" 目标镜像名：[标签名]#镜像的提交

#容器命令
$docker run [OPTIONS] IMAGE [COMMAND]
#[OPTIONS] --name:容器指定名称 -d:后台运行 -i:交互模式运行 -t:分配伪终端 -P:随机端口映射 -p:指点端口映射（hostport:containerport）
$docker run -it centos /bin/bash 
#使用镜像centos以交互模式启动一个容器,在容器内执/bin/bash命令。
$docker ps [OPTIONS]  #列出所有正在运行的容器
#-a :列出当前所有正在运行的容器+历史上运行过的
#-l :显示最近创建的容器。
#-n：显示最近n个创建的容器。
#-q :静默模式，只显示容器编号。
#--no-trunc :不截断输出
exit #容器停止退出  
crtl+P+Q#容器不停止退出
$docker start 容器ID或者容器名 #启动容器
$docker restart 容器ID或者容器名 #重启容器
$docker stop 容器ID或者容器名 #停止容器
$docker kill 容器ID或者容器名 #强制停止容器
$docker rm -f $(docker ps -a -q) #一次性删除多个容器

#进入正在运行的容器并以命令交互
$docker exec -it 容器ID bashShell#会启动新的进程
$docker attach 容器ID#不会开启新的进程

#从容器内拷贝文件到主机上
$docker cp 容器ID：容器内路径 目的主机路径

#docker-machine 是docker官方提供的docker管理工具
$ docker-machine version 查看docker-machine版本
$ docker-machine create -d virtualbox default
$ docker-machine create --engine-registry-mirror=https://opl93tto.mirror.aliyuncs.com -d virtualbox default2 #创建machine
$docker-machine ls  #查看docker
$docker-machine env vm_docker #vm的环境变量
```



