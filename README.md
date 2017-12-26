## 安装vmware和centos
* 最好安装kernel是3.10及以上的kernel。

## 安装docker 
### yum install  docker-io

安装的清单如下：
```
Dec 26 06:33:17 Installed: yajl-2.0.4-4.el7.x86_64
Dec 26 06:33:17 Installed: 1:oci-systemd-hook-0.1.14-1.git1ba44c6.el7.x86_64
Dec 26 06:33:18 Installed: 2:oci-umount-2.3.0-1.git51e7c50.el7.x86_64
Dec 26 06:33:18 Installed: setools-libs-3.3.8-1.1.el7.x86_64
Dec 26 06:33:18 Installed: 1:oci-register-machine-0-3.13.gitcd1e331.el7.x86_64
Dec 26 06:33:18 Installed: container-storage-setup-0.8.0-3.git1d27ecf.el7.noarch
Dec 26 06:33:18 Installed: checkpolicy-2.5-4.el7.x86_64
Dec 26 06:33:18 Installed: libcgroup-0.41-13.el7.x86_64
Dec 26 06:33:18 Installed: python-IPy-0.75-6.el7.noarch
Dec 26 06:33:18 Installed: 1:skopeo-containers-0.1.26-2.dev.git2e8377a.el7.centos.x86_64
Dec 26 06:33:18 Installed: audit-libs-python-2.7.6-3.el7.x86_64
Dec 26 06:33:18 Installed: libsemanage-python-2.5-8.el7.x86_64
Dec 26 06:33:18 Installed: policycoreutils-python-2.5-17.1.el7.x86_64
Dec 26 06:33:39 Installed: 2:container-selinux-2.33-1.git86f33cd.el7.noarch
Dec 26 06:33:39 Installed: 2:docker-common-1.12.6-68.gitec8512b.el7.centos.x86_64
Dec 26 06:33:39 Installed: 2:docker-client-1.12.6-68.gitec8512b.el7.centos.x86_64
Dec 26 06:33:41 Installed: 2:docker-1.12.6-68.gitec8512b.el7.centos.x86_64
```

### 查看docker版本
 docker -v
```html
Docker version 1.12.6, build ec8512b/1.12.6
```

##  配置docker镜像代理地址
参考 https://www.daocloud.io/mirror#

### 拉取rabbitmq镜像

```html
[root@localhost ~]# docker pull rabbitmq:management
Trying to pull repository docker.io/library/rabbitmq ... 
management: Pulling from docker.io/library/rabbitmq

e7bb522d92ff: Already exists 
ad90649c4d84: Already exists 
5a318b914d6c: Already exists 
cedd60f70052: Already exists 
f4ec28761801: Already exists 
b8fa44aa9074: Already exists 
e3b16d5314a0: Already exists 
7d93dd9659c8: Already exists 
356c2fc6e036: Already exists 
3f52408394ed: Already exists 
7c89a0fb0219: Already exists 
9313c22c63d5: Pull complete 
c21bcdaa555d: Pull complete 
Digest: sha256:c7466443efc28846bb0829d0f212c1c32e2b03409996cee38be4402726c56a26

```
###  运行 rabbitmq
docker run -d --name rabbitmq --publish 5671:5671 --publish 5672:5672 --publish 4369:4369 --publish 25672:25672 --publish 15671:15671 --publish 15672:15672  rabbitmq:management

0ad5a16b119bf276710c0cb8f576f86f7f251c0e4a08372dbaa43373d8d9cd33


### 确认运行

浏览器访问rabbitmq管理页面  http://192.168.247.131:15672/

###  创建vhost
在上述管理页面的vhost选项卡中创建name为dev 的vhost


