## 谷粒商城

## linux环境搭建

visualBox进行安装需要cpu开启虚拟化，在开机启动的时候设置主板，CPU configuration，然后点击Intel Vitualization Technology。重启电脑

普通安装linux虚拟机太麻烦，可以利用vagrant可以帮助我们快速地创建一个虚拟机。主要装了vitualbox，vagrant可以帮助我们快速创建出一个虚拟机。他有一个镜像仓库。

去https://www.vagrantup.com/ 下载vagrant安装，安装后重启系统。cmd中输入vagrant有版本代表成功了。

输入`vagrant init centos/7`，即可初始化一个centos7系统。（注意这个命令在哪个目录下执行的，他的Vagrantfile就生成在哪里）

`vagrant up`启动虚拟机环境。

启动后出现default folder:/cygdrive/c/User/… =>/vagrant。然后ctrl+c退出

前面的页面中有ssh账号信息。`vagrant ssh` 就会连上虚拟机。可以使用exit退出

> 下次使用也可以直接vagrant up直接启动，但要确保当前目录在C:/用户/ 文件夹下，他下面有一个`Vagrantfile`，不过我们也可以配置环境变量。
>
> 启动后再次`vagrant ssh`连上即可

不过他使用的网络方式是网络地址转换NAT（端口转发），如果其他主机要访问虚拟机，必须由windows端口如3333断发给虚拟机端口如3306。这样每在linux里安一个软件都要进行端口映射，不方便，（也可以在virualBox里挨个设置）。我们想要给虚拟机一个固定的ip地址，windows和虚拟机可以互相ping通。

> visualBox的网络模式可以参考：https://mp.weixin.qq.com/s?__biz=MzI5MDg4ODEzOA==&mid=2247488277&idx=1&sn=012c33bec2984a61850b30b1bb270812&scene=21#wechat_redirect

- 方式1是在虚拟机中配置静态ip。

- 方式2：更改Vagrantfile更改虚拟机ip，修改其中的`config.vm.network "private_network",ip:"192.168.56.10"`，这个ip需要在windows的ipconfig中查到vitualbox的虚拟网卡ip，然后更改下最后一个数字就行（不能是1，1是我们的主机）。配置完后vagrant reload重启虚拟机。在虚拟机中`ip addr`就可以查看到地址了。互相ping也能ping通。

- 关掉防火墙，VirualBox中第一个网卡设置NAT，第二个网卡设置仅主机

- 如果ping不了baidu

  - cd /etc/sysconfig/network-scripts

  - ls 一般有ifcfg-eth0 1

  - ip addr 看哪个网格是192.168.56网段，然后vim他

  - vim ifcfg-eth1 加入

    ```sh
    GATEWAY=192.168.56.1
    DNS1=114.114.114.114
    DNS2=8.8.8.8
    ```

  - service network restart

默认只允许ssh登录方式，为了后来操作方便，文件上传等，我们可以配置允许账号密码登录

```sh
vim /etc/ssh/sshd_config
修改
PasswordAuthentication yes
重启
service sshd restart
账号root
密码vagrant
```

配置源

```sh
# 备份原yum源

mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
# 使用新yum源
curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.163.com/.help/CentOS7-Base-163.repo
# 生成缓存
yum makecache
```

##### 虚拟机安装docker

https://docs.docker.com/engine/install/centos/

```bash
#卸载系统之前的docker 
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
                  
                  
sudo yum install -y yum-utils

# 配置镜像
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
    
sudo yum install docker-ce docker-ce-cli containerd.io

sudo systemctl start docker
# 设置开机自启动
sudo systemctl enable docker

docker -v
sudo docker images

# 配置镜像加速
```

https://cr.console.aliyun.com/cn-qingdao/instances/mirrors

根据页面命令执行完命令

```bash
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://chqac97z.mirror.aliyuncs.com"]
}
EOF

sudo systemctl daemon-reload
sudo systemctl restart docker
```

##### 安装mysql-docker

用docker安装上mysql，去docker仓库里搜索mysql

```bash
sudo docker pull mysql:5.7

# --name指定容器名字 -v目录挂载 -p指定端口映射  -e设置mysql参数 -d后台运行
sudo docker run -p 3306:3306 --name mysql \
-v /mydata/mysql/log:/var/log/mysql \
-v /mydata/mysql/data:/var/lib/mysql \
-v /mydata/mysql/conf:/etc/mysql \
-e MYSQL_ROOT_PASSWORD=root \
-d mysql:5.7
su root 密码为vagrant，这样就可以不写sudo了
[root@localhost vagrant]# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                               NAMES
6a685a33103f        mysql:5.7           "docker-entrypoint.s…"   32 seconds ago      Up 30 seconds       0.0.0.0:3306->3306/tcp, 33060/tcp   mysql
```

> 注：请不要再告诉我mysql的配置文件是my.conf 哈市my.cnf的问题了，我觉得这个问题是跟mysql版本和linux版本有关系，你自己看下你系统里的配置文件样式就可以了

```bash
# 进入已启动的容器
docker exec -it mysql bin/bash
# 退出进入的容器
exit;

因为有目录映射，所以我们可以直接在镜像外执行
vi /mydata/mysql/conf/my.conf 

[client]
default-character-set=utf8
[mysql]
default-character-set=utf8
[mysqld]
init_connect='SET collation_connection = utf8_unicode_ci'
init_connect='SET NAMES utf8'
character-set-server=utf8
collation-server=utf8_unicode_ci
skip-character-set-client-handshake
skip-name-resolve

保存(注意评论区该配置不对，不是collection而是collation)

docker restart mysql
```

> 如何通过其他工具链接ssh
>
> 修改/etc/ssh/sshd_config
>
> 修改 PasswordAuthentication yes
>
> systemctl restart sshd.service 或 service sshd restart
>
> 连接192.168.56.10:22端口成功，用户名root，密码vagrant
>
> 也可以通过vagrant ssh-config查看ip和端口，此时是127.0.0.1:2222

##### Redis

如果直接挂载的话docker会以为挂载的是一个目录，所以我们先创建一个文件然后再挂载，在虚拟机中。

```bash
# 在虚拟机中
mkdir -p /mydata/redis/conf
touch /mydata/redis/conf/redis.conf

docker pull redis

docker run -p 6379:6379 --name redis \
-v /mydata/redis/data:/data \
-v /mydata/redis/conf/redis.conf:/etc/redis/redis.conf \
-d redis redis-server /etc/redis/redis.conf

# 直接进去redis客户端。
docker exec -it redis redis-cli
```

默认是不持久化的。在配置文件中输入appendonly yes，就可以aof持久化了。修改完docker restart redis，docker -it redis redis-cli

```bash
vim /mydata/redis/conf/redis.conf
# 插入下面内容
appendonly yes
保存

docker restart redis
```

设置redis容器在docker启动的时候启动

```shell
docker update redis --restart=always
```

#### 安装nginx docker

安装nginx为P124的内容

```bash
docker pull nginx:1.10
# 随便启动一个nginx实例，只是为了复制出配置，放到docker里作为镜像的统一配置
docker run -p 80:80 --name nginx -d nginx:1.10

# 把nginx里的东西复制出来
cd /mydata/nginx
docker container cp nginx:/etc/nginx .
然后在外部 /mydata/nginx/nginx 有了一堆文件
mv /mydata/nginx/nginx /mydata/nginx/conf
# 停掉nginx
docker stop nginx
docker rm nginx

# 创建新的nginx，使用刚才复制出来的配置文件
docker run -p 80:80 --name nginx \
-v /mydata/nginx/html:/usr/share/nginx/html \
-v /mydata/nginx/logs:/var/log/nginx \
-v /mydata/nginx/conf:/etc/nginx \
-d nginx:1.10

# 注意一下这个路径映射到了/usr/share/nginx/html，我们在nginx配置文件中是写/usr/share/nginx/html，不是写/mydata/nginx/html

docker update nginx --restart=always
```

测试

```bash
cd /mydata/nginx/html/
vim index.html
随便写写
测试 http://192.168.56.10:80
```

