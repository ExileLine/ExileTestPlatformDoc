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
requirepass 123456

如果需要外部连接
1.修改 
  protected-mode 为 no

2.修改(docker部署的服务不要修改这个) 
    bind 127.0.0.1 为 bind 0.0.0.0
        
3.注释
    bind 127.0.0.1 ::1
```

### 启动相关

带配置文件以守护进程方式启动

```shell
cd redis-6.0.0/src
```

```shell
./redis-server /srv/redis-6.0.0/redis.conf &
```
	
	

