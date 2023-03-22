# 项目部署

### 安装`git`以及拉取项目

```shell
apt-get install git -y
git --version
```

```shell
cd /srv

web端:
    git clone https://github.com/ExileLine/ExileTestPlatformWeb.git
    
server端:
    git clone https://github.com/ExileLine/ExileTestPlatformServer.git
```

### 数据库相关

自行准备或参考如下安装

- Mysql（`5.7`，`8.0`，或以上）

    - 参考：[数据库安装](./install_mysql_or_mariadb.md)


- Redis（`5.0`，`6.0`，或以上）

    - 参考：[Redis安装](./install_redis.md)

### Web端部署

- 方法一：`本地`完成`npm`打包后放置服务器对应的目录下。
    ```shell

    ```  
- 方法二：`服务器`完成`npm`打包后放置对应的目录下。
    ```shell

    ``` 

### Server端部署

#### 安装相关依赖

`Debian(9,10,11)` 或 `Ubuntu(18,20,21)`

```shell
sudo apt update -y
sudo apt-get update
sudo apt-get upgrade -y
sudo apt install wget
sudo apt install gcc -y
sudo apt install build-essential zlib1g-dev libssl-dev libncurses5-dev libreadline-dev libgdbm-dev libnss3-dev libffi-dev -y
```

`CentOS(7)`

```shell
sudo yum update
sudo yum -y install wget gcc atuomake
sudo yum -y install devtoolset-9-gcc devtoolset-9-gcc-c++ devtoolset-9-binutils
sudo yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel python3-devel libffi-devel epel-release centos-release-scl
sudo yum install -y gcc-c++ libstdc++-static ant cmake byacc flex automake libtool binutils-devel bison ncurses-devel gcc kernel-devel libatomic
```

#### 安装Python3

- [传送门](./install_python.md)

#### 安装`Pipenv`虚拟环境管理

PS：如果使用非`3.9.4`版本，则需要修改 `/ExileTestPlatformServer/Pipfile` 中的 `python_version`版本号后继续往后的操作

```shell
pip install pipenv
或:
pip install pipenv -i https://pypi.doubanio.com/simple
```

#### 安装`Celery`异步任务

```shell
pip install celery
或:
pip install celery -i https://pypi.doubanio.com/simple
```

#### 安装`Nginx`以及配置文件

```shell
安装:
    apt-get install nginx

查看版本:
    nginx -v
```

参照下图修改`/ExileTestPlatformServer/exile_nginx_for_server.conf`配置文件，复制到服务器`/etc/nginx/conf.d`中

- ![exile_cover](imgs/nginx_docs.png)

    ```shell
    重启Nginx:
        nginx -s reload
    ```

#### 宿主机部署(如果使用`docker`部署忽略此步骤)

- 安装`Uwsgi`

    - 参考：https://juejin.cn/post/6844903870250876935

#### Docker部署(如果使用`宿主机`部署忽略此步骤)

- 安装`Docker`并部署以及`Dockerfile`
  ```shell
  安装:
      wget -qO- https://get.docker.com/ | sh
  ```

### 启动相关

#### 使用Docker启动

- 启动`Docker`快捷启动脚本 [server_start.sh](server_start.sh) 根据需要配置好对应的容器卷映射后执行即可。

  ```shell
  cd /目录/ExileTestPlatformServer
  sh server_start.sh
  ```

#### 宿主机启动

```shell
cd /目录
uwsgi --ini /ExileTestPlatformServer/exile_uwsgi_for_server.ini
```

#### 启动`Celery`异步任务

```shell
cd /目录/ExileTestPlatformServer

进入env:
    pipenv shell
```

后台启动例子，其他启动命令查阅 `/ExileTestPlatformServer/celery_app.py`（先创建好目录，如：/srv/logs）

```shell
celery -A celery_app.cel multi start worker --pidfile="/srv/logs/celery/%n.pid" --logfile="/srv/logs/celery/%n%I.log"
```