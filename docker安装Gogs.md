一、安装docker和使用
1、更新apt-get源:   sudo apt-get update
2、安装docker:      sudo apt-get install docker.io
3、重启docker:      sudo service docker restart
4、查看docker状态：  sudo service docker status
5、运行docker：     sudo service docker start
6、停止docker：     sudo service docker stop
二、docker安装mysql
1、搜索一下mysql: docker search mysql
2、拉取mysql镜像： sudo docker pull mysql:latest
3、启动mysql：docker run -d -p 13306:3306  --name mysql2 -v /opt/mydata/:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 mysql:latest
含义是：生成名为mydql2的docker镜像，在后台执行，root账号的密码为123456,将容器的端口3306映射到宿主端口13306
4、查看已经运行容器CONTAINER ID  sudo docker ps 
5、进入mysql容器 sudo docker exec -it 1a8707b7ef5f /bin/bash
6、登陆mysql: mysql -u root -p 输入密码
7、创建gogs数据库: mysql> CREATE DATABASE gogs CHARACTER SET utf8 COLLATE utf8_bin;
8、查看当前存在什么数据库：mysql> show databases;
9、选择gogs数据库：mysql> use gogs
10、查询gogs数据库存在什么表：mysql> show tables;
11、选择查看表：mysql> select * from user;
12、退出mysql: mysql> QUIT;
13、退出docker：exit;

三、docker安装gogs
在此之前,先在mysql中创建gogs数据库. [注意,一定要先将mysql数据库的默认字符编码设置为utf8, 否则, gogs在自动创建表时, 会出现问题]

1、搜索一下gogs：   sudo docker search gogs
2、拉取Gogs镜像：   sudo docker pull gogs/gogs:latest
3、创建Gogs物理位置： sudo mkdir -p /var/gogs
4、启动gogs:     docker run -d --name=mygogs -p 10022:22 -p 10080:3000 -v /var/gogs:/data gogs/gogs
参数说明:
-d: 后台方式运行容器
-p: 端口映射, 将容器的22端口映射到宿主机的10022端口, 将容器的3000端口映射到宿主机的10080端口
--name: 指定容器名称
-v: 数据卷挂载, 用于将容器和数据分离

四、打开浏览器 http://ip:10080 初始化配置 mysql 

