# Redis安装

### 安装(以6.0版本为例)

下载

```shell
wget http://download.redis.io/releases/redis-6.0.0.tar.gz
```

解压

```shell
tar -xvf redis-6.0.0.tar.gz
```

编译

```shell
cd redis-6.0.0
make
```

### 配置相关

修改配置

```shell
cd redis-6.0.0
```

```shell
vim redis.conf

修改密码:
requirepass 你的密码
```

### 启动相关

带配置文件以守护进程方式启动

```shell
cd redis-6.0.0/src
```

```shell
cd /redis-6.0.0/src
./redis-server /srv/redis-6.0.0/redis.conf &
```
	
	

