# 指令集

# 视频

## 平台指令_下发

### (201-203/105-107)

#### 清空指令窗

```bash
clear
```

### 进入bin目录

##### 203下需要切换用户 → hcicloud

```txt
su - hcicloud
```

##### -iwatch

```bash
cd /home/iwatch/cloud/avr_stream/bin/
```

##### -hcicloud

```bash
cd /home/hcicloud/cloud/avr_stream/bin/
```

#### bin目录下指令

##### 启动平台（200-202）

```bash
./runs_avr_video -d
```

##### 启动平台（203）

```bash
bash run.sh
```

##### 查进程

```bash
ps -ef | grep runs
```

#### 杀进程（pid：进程号）

```bash
killall runs_avr_video
```

```bash
kill -9
```

##### 查看日志

```bash
tail -f ../log/avr_video.log
```

##### 查看配置文件

```bash
cat ../conf/avr_video.conf
```

##### 修改配置文件

```bash
vi ../conf/avr_video.conf
```

## inspectmodel模块指令集(147/148)

负责和引擎交互，利用mq传递信息

#### inspectmodel目录下指令

##### 进入inspectmodel路径

```bash
cd /home/inspectmodel
```

##### 查看inspectmodel日志

```bash
tail -f nohup.out
```

##### 查看inspectmodel日志 前1000行

```bash
tail -f nohup.out -n 1000
```

#####  

##### 启动inspectmodel的jar包

```bash
nohup java -jar inspectmodel-1.jar &
```

##### 查看inspectmodel进程

```bash
ps -ef | grep inspectmodel-1.jar
```

##### 删除inspectmodel.jar进程

```bash
kill -9
```

## jar包指令集

##### 查看inspectmodel进程

```bash
ps -ef | grep .jar
```

##### 删除inspectmodel.jar进程

```bash
kill -9
```

##  引擎指令(44)

#### 清空指令窗

```bash
clear
```

#### 查进程

```bash
ps -ef | grep iWatchServer
```

#### 杀进程（pid：进程号）

```bash
kill -9
```

```bash
killall iWatchServer
```

```bash
killall iWatchServer1
```

```bash
killall iWatchServer2
```

```bash
killall iWatchServer3
```

```bash
killall iWatchServer4
```

```bash
killall iWatchServer5
```

```bash
killall iWatchServer6
```

```bash
killall iWatchServer7
```

#### 查引擎GPU容量

```bash
nvidia-smi
```

### 进入bin目录

##### -cloud~cloud7

```bash
cd /home/hcicloud/cloud/avr_engine/bin
```

```bash
cd /home/hcicloud/cloud1/avr_engine/bin
```

```bash
cd /home/hcicloud/cloud2/avr_engine/bin
```

```bash
cd /home/hcicloud/cloud3/avr_engine/bin
```

```bash
cd /home/hcicloud/cloud4/avr_engine/bin
```

```bash
cd /home/hcicloud/cloud5/avr_engine/bin
```

```bash
cd /home/hcicloud/cloud6/avr_engine/bin
```

```bash
cd /home/hcicloud/cloud7/avr_engine/bin
```

#### bin目录下指令

##### 启动引擎（cloud1 路径 ~ cloud7路径）

```bash
bash start.sh
```

##### 启动引擎（cloud 路径）

```bash
./iWatchServer -d
```



## MQ指令(147,148)

### 147服务器

#### 进入mq启动路径

```bash
cd /home/apache-activemq-5.16.0/bin
```

#### 启动

```bash
./activemq start
```

### 148服务器

#### 进入mq启动路径

```bash
cd /home/apache-activemq-5.16.0/bin
```

#### 启动

```bash
./activemq start
```

### 查看bash进程

```bash
ps -ef | grep .jar
```

### 

## VQS模块启动(83/84)

### 查询模块进程

```bash
ps -ef | grep .jar
```

### 进入模块

#### 进入路径

```bash
cd /home/analysis
```

```bash
cd /home/distribution
```

```bash
cd /home/exception
```

```bash
cd /home/statistics
```

```bash
cd /home/management
```

#### 启动模块

```bash
nohup java -jar analysis-1.0-SNAPSHOT.jar &
```

```bash
nohup java -jar distribution-1.0-SNAPSHOT.jar &
```

```bash
nohup java -jar exception-info-1.0-SNAPSHOT.jar &
```

```bash
nohup java -jar statistics-1.0-SNAPSHOT.jar &
```

```bash
nohup java -jar management-1.0-SNAPSHOT.jar &
```

#### 查看日志

```bash
tail -f nohup.out
```

```bash
tail -f nohup.out -n 1000
```

#### 修改配置

```bash
vim application.yml
```



## 录视频指令(硬盘已寄出)

### 进入bin目录(200-203)

```bash
cd /data/output/bin
```

### 进入bin目录(105-107)

```bash
cd /app/output/bin
```

### 启动脚本+文件名.sh

```bash
bash 
```

### 查看bash进程

```bash
ps -ef | grep bash
```

### 删除0fp视频文件

```bash
rm -rf record/*0fps*
```

### 查看录像更新情况

```bash
ll record/ -h
```

### 添加一个视频摄像头+摄像头编号

 ```bash
./test_stream -log 5 -save -dev  
 ```



## Oracle相关指令

### 重启-85.21

```bash
cd ~
```

#### 切换Oracle用户

```bash
su - oracle
```

#### 以操作系统权限认证的oracle sys管理员登陆

```bash
sqlplus / as sysdba
```

#### 关闭数据库

```bash
shutdown immediate
```

#### 开启数据库

```bash
startup
```



## 本地视频推流

#### 视频路径(10.90.85.44)

```bash
/home/hcicloud/testVideo/
```

#### 按营业厅分类

```txt
/home/hcicloud/testVideo/benpao_1.mp4
```

```bash
/home/hcicloud/testVideo/chouyan.mp4
```

```bash
/home/hcicloud/testVideo/chouyan1.mp4
```

```bash
/home/hcicloud/testVideo/dadianhua.mp4
```

```bash
/home/hcicloud/testVideo/dajia.mp4
```

```bash
/home/hcicloud/testVideo/eat_4.mp4
```

```bash
/home/hcicloud/testVideo/huanjingweisheng.mp4
```

```bash
/home/hcicloud/testVideo/juji.mp4
```

```bash
/home/hcicloud/testVideo/paihuai_1.mp4
```

```bash
/home/hcicloud/testVideo/shuaidao_1.mp4
```

```bash
/home/hcicloud/testVideo/wanshouji_4.mp4
```

```bash
/home/hcicloud/testVideo/yiliuwu_5.mp4
```

```bash
/home/hcicloud/testVideo/zhedang_1.mp4
```

```bash
/home/hcicloud/testVideo/zhuzu_1.mp4
```



## RTSP服务搭建+运行

### 所在服务器

```bash
10.90.86.84
```

### 解压

```bash
tar xvzf live555rtsp.tar.gz
```

### 运行(后台运行)

```bash
./live555MediaServer LIVE555 Media Server &
```

标红处为rtsp路径，把支持的文件名放在程序同一级即可。例如用vlc访问 rtsp:// rtsp://10.0.1.16:8554/test.264(默认端口是8554)

#### 查看服务进程

```bash
ps -ef | grep live555MediaServer
```

#### 查看服务端口

```bash
netstat -nap | grep 12340
```

#### 视频地址

##### 例如用vlc访问 

```txt
rtsp://10.90.86.84/test3.264
```

### 注意

##### 本地视频文件需要使用ffmpeg进行转码成支持的格式，具体命令如下：

```bash
ffmpeg -i run.mp4 -vcodec h264 run.264
ffmpeg -i out.ogv -vcodec mpeg4 out.mp4
ffmpeg -i out.ogv -vcodec libxvid out.mp4
ffmpeg -i out.mp4 -vcodec wmv1 out.wmv
ffmpeg -i out.mp4 -vcodec wmv2 out.wmv
```





# 语音



## Vncviewer相关

### sql

```bash
bash /home/hcicloud/sqldeveloper/sqldeveloper.sh
```

### 关掉指定用户(推荐)

```bash
vncserver -kill :3
```

```bash
vncserver -kill :4
```

### 进程关闭Vncserver

```bash
ps -ef|grep -i vnc
```

```bash
kill -9 对应用户的进程id
```

### 启动指定用户

```bash
vncserver :3
```

```bash
vncserver :4
```

### 配置

```bash
vim /etc/sysconfig/vncservers
```

### 进程

```bash
ps -ef | grep vnc
```

```bash
zhj :4
hcicloud
```



## sszj+cti 启动+配置

#### 打开目录

```bash
cd /home/hcicloud/yyzj2nd/sszj
```

```bash
cd /home/hcicloud/yyzj2nd/myCti
```

#### 配置yml

```bash
vim application.yml
```

#### 配置properties

```bash
vim system.properties
```

#### 查jar进程

```bash
ps -ef | grep .jar
```

#### 看日志

##### 查看mycti

```bash
tail -f /home/hcicloud/yyzj2nd/myCti/logs/info
```

```bash
tail -f /home/hcicloud/yyzj2nd/myCti/logs/error
```

##### 查看sszj (即：RealTimeDemo)

```bash
tail -f nohup.out
```

#### 启动

```bash
bash run.sh
```

#### 关闭

```bash
bash shutdown.sh
```

#### run.sh (开启脚本)

```bash
nohup /home/jdk1.8.0_171/bin/java -Xms2G -Xmx2G -jar sszj.jar &
```

#### shutdown.sh (关闭脚本)

```bash
ps -ef|grep sszj.jar|grep -v grep|cut -c 9-15|xargs kill -s 9
```

```bash
ps -ef|grep elasticsearch|grep -v grep|cut -c 9-15|xargs kill -s 9
```



## 登录服务器

#### 切换用户(85.22)

账密来自 "服务器台账.xls"

##### 账号

```txt
primjh
```

密

```txt
prime@sinovoice.INSPECT.22
```

指令

```bash
sudo -i
```

```bash
prime@sinovoice.INSPECT.22
```

```bash
su - hcicloud
```



## 启动ES(86.83 / 86.84)

### 切换到非Root用户

##### （su - 和 su在于前者切换了环境变量，后者是全局环境变量）

```bash
su - hcicloud
```

### 开启es

#### 切换路径

```bash
cd /home/hcicloud/es/elasticsearch-7.8.0/bin
```

#### 启动ES

```bash
./elasticsearch -d
```

#### 查询进程

```bash
ps -ef | grep elasticsearch
```



## ES集群配置

### 进入es路径

```bash
cd /home/es
```

### 进入elasticsearch路径

```bash
cd /home/es/1elasticsearch/
```

```bash
cd /home/es/2elasticsearch/
```

```bash
cd /home/es/3elasticsearch/
```

```bash
cd /home/es/4elasticsearch/
```

```bash
cd /home/es/5elasticsearch/
```

### 配置elasticsearch

##### 10.90.90.10/10.90.86.84

```bash
vim 1elasticsearch/config/elasticsearch.yml
```



## 抓包程序配置+启动

### 进入bin目录

#### 10.90.124.90(只能抓到客服一部)

```bash
cd /home/hcicloud/cloud/bin
```

#### 10.90.124.83/10.90.124.84

```bash
cd /home/speech/cloud_bak6/bin
```

#### 查看log(bin目录下)

```bash
vim ../log/speech_capture_log.log
```

#### 查看配置文件(bin目录下)

```bash
vim ../conf/speech_capture.conf
```

### 查看抓包进程

```bash
ps -ef |grep speechcapture
```

#### run.sh (开启脚本)

```bash
export LD_LIBRARY_PATH=$(pwd):$LD_LIBRARY_PATH
export HCICLOUD_HOME=$(pwd)/../
nohup ./speechcapture -w -W >/dev/null &
```

#### shutdown.sh (关闭脚本)

```bash
ps -ef|grep speechcapture|grep -v grep|cut -c 9-15|xargs kill -s 9
```



# 公共

## 配置java环境变量

### (推荐)修改.bash_profile文件（局部——用户级别）

#### 打开.bash_profile文件

```bash
cd ~
```

```bash
vim .bash_profile
```

#### 在.bash_profile文件末尾加入：

```bash
export JAVA_HOME=/home/hcicloud/jdk1.8.0_291
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```

#### 加载配置文件

```bash
source .bash_profile
```



### (不推荐)修改/etc/profile文件（全局——所有用户）

#### 打开/etc/profile

```bash
vim /etc/profile
```

#### 在profile文件末尾加入

```bash
export JAVA_HOME=/usr/share/jdk1.6.0_14
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```

#### 加载配置文件

```bash
source /etc/profile
```



## 用户登录/用户配置

#### 登录服务器

##### 切换用户(10.90.86.83)

账密来自 "服务器台账.xls"

##### 账号

```txt
root
```

密

```txt
Flzx#3000c@rlgl
```

指令

```bash
sudo -i
```

```bash
Flzx#3000c@rlgl
```

```bash
su - hcicloud
```

#### 修改密码

用户切换

```bash
su - root
```

```bash
Flzx#3000c@rlgl
```

修改对应用户密码（以 hcicloud为例）

```bash
passwd hcicloud
```

#### 新增用户

sinovoice为例

```bash
useradd sinovoice
```

```bash
passwd sinovoice
```



## firewalld防火墙设置

--zone 作用域  | --add-port=3690/tcp 添加端口，格式为：端口/通讯协议

--permanent 永久有效，没有此参数重启防火墙后失效

### #查看firewall的状态

```bash
firewall-cmd --state
```

### #查看防火墙规则

##### （只显示/etc/firewalld/zones/public.xml中防火墙策略）

```bash
firewall-cmd --list-all
```

### 开启防火墙

```bash
systemctl start firewalld
```

### 关闭防火墙

```bash
systemctl stop firewalld
```

### 开放指定端口

```bash
firewall-cmd --zone=public --add-port=3690/tcp --permanent
firewall-cmd --zone=public --add-port=18443/tcp --permanent
firewall-cmd --zone=public --add-port=9200/tcp --permanent
firewall-cmd --zone=public --add-port=9300/tcp --permanent
firewall-cmd --zone=public --add-port=9201/tcp --permanent
firewall-cmd --zone=public --add-port=16363/tcp --permanent
firewall-cmd --zone=public --add-port=18787/tcp --permanent
firewall-cmd --zone=public --add-port=8082/tcp --permanent
firewall-cmd --zone=public --add-port=8082/tcp --permanent
firewall-cmd --zone=public --add-port=12521/tcp --permanent
```

### 开放指定IP与端口

```bash
firewall-cmd --zone=public --permanent --add-rich-rule 'rule family="ipv4" source address="10.90.79.187" port port=10521 protocol="tcp" accept'
```

### 开放指定IP端

```bash
firewall-cmd --add-rich-rule="rule family="ipv4" source address="192.168.2.0/24" port protocol="tcp" port="5432" accept" --permanent
```

### 删除规则

```bash
firewall-cmd --remove-rich-rule="rule family="ipv4" source address="10.90.79.187" protocol="tcp" port="9200" accept" --permanent
```

### 重新加载配置文件

```bash
firewall-cmd --reload
```

### 重新启动firewall服务

```bash
systemctl restart firewalld.service
```

### 查看端口号

查看当前所有tcp端口

```bash
netstat -ntlp
```

查看所有 指定 端口

```bash
netstat -ntulp | grep 3690
```



## SVN启动/安装/配置

### 启动svn

```bash
svnserve -d -r /home/sinovoice/svn/project/ --listen-port=3690
```

### 查看svnserve进程

```bash
ps -ef | grep svnserve
```

### 安装svn依赖

```bash
yum install subversion
```



## SVN移植

### 前言

```txt
公司以前用的SVN是安装在windows2003下，用了一年多，现在大家觉得很慢，强烈要求改成linux平台。在linux下安装subversion还是挺简单的，就不多说了，很快就装好了。现在问题来了，怎么把windows平台的svn数据迁移到linux平台呢？我想他们的存储格式不一样，svn版本也不一样，应该不能直接拷贝repository下的库文件，由于时间关系就没有做这样的测试。在网上查了下资料，用dump load就行
```

### 详细步骤：

### 导出VisualSVN仓库

```bash
svnadmin dump /opt/svn/projectshop > /dev/shm/svnRepository/projectshop_20210507
```

### 在被移植端create相同名称的仓库

```bash
mkdir -p 目标路径的仓库地址
```

```bash
svnadmin create 目标路径的仓库地址
```

### 在被移植端load 导出的库文件(.dump)

```bash
cd /data/svnrepos 
```

```bash
svnadmin load /home/sinovoice/svn/project < /home/sinovoice/svn/projectshop_20210507
```



## Iptables安装与配置

### 10.90.86.83

### 配置iptables

```bash
vim /etc/sysconfig/iptables
```

### 查看状态

centOS 7下 使用systemctl操作

```bash
systemctl status iptales
```

### 开启服务

```bash
systemctl start iptables
```

### 停止服务

```bash
systemctl stop iptables
```

### 重启（root下修改以后，需重启）

CentOS 7下指令

```bash
systemctl restart iptables
```

老版本：service iptables restart

### 查看规则列表

```bash
iptables -L
```

### 关键字查询iptables_含端口

```bash
cat /etc/sysconfig/iptables | grep 79.187
```

### 关键字查询iptables_无端口

```bash
iptables -L | grep key
```

### 重新加载一个服务的配置文件

```bash
sudo systemctl reload iptables
```

###配置规则

```bash
iptables -A OUTPUT -d 10.90.79.187/32 -j ACCEPT
iptables -A INPUT -s 10.90.79.187/32 -p tcp -m tcp --dport 9200 -j ACCEPT
iptables -A OUTPUT -s 10.90.79.187/32 -p tcp -m tcp --dport 9200 -j ACCEPT

iptables -A INPUT -s 10.90.79.187/32 -j DROP
```

### ES内网环境安全策略

共五种方案——出自【漏洞-20210916-067（总第03067号）-10.90.86.83存在elasticsearch未授权访问漏洞整改通知单】

```bash
1、为elasticsearch增加登录验证，可以使用官方推荐的shield插件，该插件为收费插件，可试用30天，免费的可以使用elasticsearch-http-basic，searchguard插件。插件可以通过运行Biplugin install [github-name]/repo-name。同时需要注意增加验证后，请勿使用弱口令。
2、架设nginx反向代理服务器，并设置http basic认证来实现elasticsearch的登录认证。
3、默认开启的9200端口和使用的端口不对外公布，或架设内网环境。
// accept
iptables -A INPUT -p tcp -s 127.0.0.1 --dport 9200 -j ACCEPT
iptables -A INPUT -p udp -s 127.0.0.1 --dport 9200 -j ACCEPT
iptables -A INPUT -p tcp -s 10.90.79.187 --dport 9200 -j ACCEPT
iptables -A INPUT -p udp -s 10.90.79.187 --dport 9200 -j ACCEPT
iptables -A OUTPUT -s 10.90.79.187/32 -p tcp -m tcp --dport 9200 -j ACCEPT
iptables -A OUTPUT -s 10.90.79.187/32 -p udp -m udp --dport 9200 -j ACCEPT
// drop
iptables -I INPUT -p tcp --dport 9200 -j DROP
iptables -I INPUT -p udp --dport 9200 -j DROP
// 保存规则并重启 iptables
service iptables save
service iptables restart

4、elasticsearch 早期版本在“CVE中文漏洞信息库”网站上已有部分漏洞被披露，建议使用1.7.1以上版本或使用最新版本程序。
5、限制IP访问，绑定固定IP
6、为elasticsearch增加登录验证，可以使用官方推荐的shield插件，该插件为收费插件，可试用30天，免费的可以使用elasticsearch-http-basic，searchguard插件。插件可以通过运行Biplugin install [github-name]/repo-name。同时需要注意增加验证后，请勿使用
```





## 查看Linux系统 版本

### 查看Linux发行版系统版本

```bash
cat /etc/issue
```

### 查看RedHat系的Linux版本

```bash
cat /etc/redhat-release
```

### 列出所有版本信息

```bash
lsb_release -a
```



## 查看Linux磁盘余量

#### 查看磁盘剩余空间

```bash
df -hl
```

```bash
df -hl 检查路径
```

```bash
df -hl /home/hcicloud/testVideo
```

#### 查看test目录所占空间

```bash
du -h 路径
```

```bash
du -h /home/hcicloud/testVideo
```



## 查看Linux网卡速度

查询网卡信息（eth0-eth9，bond0-bond9）

```bash
ifconfig
```

ethtool查询网卡详情（X的值为0-9）

```bash
ethtool emX
```

```bash
ethtool ethX
```



## Linux文件下载/上传

### 上传文件到Linux

rz(receive zmodem) - 从本地选择文件上传到Linux服务器

```bash
rz
```

### 下载Linux文件

sz(send zmodem) - 从Linux下载到Windows系统

```bash
sz
```

## Nginx相关

### 启动nginx

配置文件用绝对路径——有些目录 不认相对路径

```bash
./nginx -c /usr/local/nginx/conf/nginx.conf
```



## 文件操作

### 解压文件

```bash
tar -zxvf 文件名 目标路径
```

### 压缩文件

```bash
tar -zcvf 文件名 目标路径
```

### 复制文件

```bash
cp 文件名 目标路径/文件名
```

### 复制目录

```bash
cp -r dir1 dir2
```



## 搜索Redis的key

### Scan搜索

查找 含有key的键，在0到5条中查找

```bash
scan 0 match *key* count 5
```

### keys搜索

```bash
keys *key*
```



### 安装配置 Telnet





# 方案集

### 内网maven实用方案：

```txt
IDEA步骤：
	- 将运行项目移植到外网环境
	- 在外网环境下载好所需 jar依赖，服务软件，自定义依赖等
	- 确保在外网项目依赖配置能支撑 项目的正常运行
	- 复制所有项目所需依赖（包括maven仓库等）到内网环境，在内网环境要用maven3（idea自带的maven管理版本，而不是自己下的，idea2018兼容不了3.5.2以上的maven，这里建议用idea自带的maven3）
	- 运行项目，将setting中maven下的repository进行update操作。运行项目。【这个功能只有 idea2018及以下版本有】
```

Idea的RunBoard配置

```xml
<component name="RunDashboard">
  <option name="configurationTypes">
    <set>
      <option value="SpringBootApplicationConfigurationType" />
    </set>
  </option>
  <option name="ruleStates">
    <list>
      <RuleState>
        <option name="name" value="ConfigurationTypeDashboardGroupingRule" />
      </RuleState>
      <RuleState>
        <option name="name" value="StatusDashboardGroupingRule" />
      </RuleState>
    </list>
  </option>
</component>
```

记录一个实战经验

```txt
出现导包失败后
我将 项目的 maven库 复制粘贴，然后改名。【备份一个是为了以防万一】
先删除 项目 的idea相关配置文件 .idea和.iml【具体编译器需要自己查询配置重置方案】
在idea打开项目，配置maven库地址，将库的地址 改为新命名的 maven仓库。
再更新repository【这个功能只有 idea2018及以下版本有】
```

### Linux删除大文件

```txt
2021年7月15日下午删除了 一个log大文件
但是没有彻底删除。下次先删进程掉 文件所在进程，再删文件

命令行查找 对应运行文件的 进程 ，删掉进程，再删掉文件
```

### 接口返回Options

```txt
2021年11月2日
因为security策略，在vue发送axios请求时，如果不更改contentType，会导致发请求发两次，而且会 将前端请求重定向 用https 发送

解决方案：将contentType 更改成 application/x-www-....   后面忘记了。 要改为 表单提交，这部分数据会以url拼接的方式 拼接到地址后面
```

# 临时区域

```bash

```



