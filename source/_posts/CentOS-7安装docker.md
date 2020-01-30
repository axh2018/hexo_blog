---
title: CentOS 7安装docker
author: 布莱恩特科比酱
top: false
cover: false
toc: false
mathjax: false
tags: docker
categories: docker
abbrlink: '748'
date: 2019-12-17 15:20:32
img:
coverImg:
password:
summary:
---

### 想必大家用CentOS都是用CentOS 7 64位的，CentOS 6和7的安装有细微区别，这里只讲下7的安装方法。昨天刚在虚拟机中CentOS 7中装了下docker，由此写这篇文章记录下这个过程.
##### 几步操作就可以搞定，看有些教程说要先卸载旧的docker，昨天试了下，我用的centos中没有旧的docker引擎，所以就直接装了。
+ 卸载旧版本(如果存在的情况下)
```shell
yum -y remove docker docker-engine docker-common docker-selinux
```
+ 安装依赖软件包
```shell
	sudo yum install -y yum-utils device-mapper-persistent-data  lvm2
```
+ 安装docker-ce
```shell	
sudo yum install docker-ce docker-ce-cli containerd.io
```
+ 启动docker
```shell
	sudo systemctl start docker
	sudo enable docker(开机自启)
```
+ 验证是否安装成功
```shell
docker --version
```

+ 阿里云镜像加速
```shell
sudo mkdir -p /etc/docker
vim /etc/docker/daemon.json
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://dttr1kms.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```

+ 卸载docker
```shell
	systemctl stop docker
	yum -y remove docker-ce
	rm -rf /var/lib/docker
```