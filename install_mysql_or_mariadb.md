# 数据库安装

## Mysql5.7

#### 安装mariadb数据库

`Debian`或`Ubuntu`

```shell
下载:
    wget --no-check-certificate https://dev.mysql.com/get/Downloads/mysql-server_5.7.31-1debian9_amd64.deb-bundle.tar
```

```shell
解压:
    tar -xvf mysql-server_5.7.31-1debian9_amd64.deb-bundle.tar
```

```shell
安装依赖:
    apt install libaio1 libnuma1 libmecab2 -y
```

```shell
依次执行:
    dpkg -i mysql-common_5.7.31-1debian9_amd64.deb

    dpkg -i mysql-community-client_5.7.31-1debian9_amd64.deb

    dpkg -i mysql-client_5.7.31-1debian9_amd64.deb

    dpkg -i mysql-community-server_5.7.31-1debian9_amd64.deb(注意：这一步，需要设置MySQL的root密码，步骤是第3步)

    dpkg -i mysql-server_5.7.31-1debian9_amd64.deb
```

#### 查看版本

```shell
mysql -V
```

#### 常用命令

```shell
启动命令  systemctl start mysql
重启命令  systemctl restart mysql
关闭命令  systemctl stop mysql
开机自起  systemctl enable mysql
关闭自起  systemctl disable mysql
查看状态  systemctl status mysql
```

## MariaDB

#### 安装mariadb数据库

`Debian`或`Ubuntu`:

```shell
sudo apt-get install mariadb-server mariadb-client
```

`CentOs`:

```shell
yum install mariadb-server 
```

#### 查看版本

```shell
mariadb -V  或  mysql -V
```

#### 常用命令

```shell
启动命令  systemctl start mariadb
重启命令  systemctl restart mariadb
关闭命令  systemctl stop mariadb
开机自起  systemctl enable mariadb
关闭自起  systemctl disable mariadb
查看状态  systemctl status mariadb
```

