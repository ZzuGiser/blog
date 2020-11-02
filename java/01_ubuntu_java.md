UBUNTU 后端学习环境配置

1 java 8 环境配置

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

2 docker 安装

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



