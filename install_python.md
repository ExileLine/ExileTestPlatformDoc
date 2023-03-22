# 安装Python3.9.4+

### 下载

```shell
进入目录(个人习惯,其他非root目录即可)
cd /srv
wget https://www.python.org/ftp/python/3.9.4/Python-3.9.4.tgz
```

### 解压

```shell
tar -zxvf Python-3.9.4.tgz
```

### 检查依赖

```shell
cd Python-3.9.4
    
Debian 或 Ubuntu:
    ./configure --enable-optimizations
    
CentOs:
    make clean
    ./configure --with-ensurepip=install
```

### 编译构建

```shell
sudo make && make install
```

```shell
查看版本:
    python3.9 --version
```

### 创建python与python3和pip软连接

PS:如果你需要使用多套Python环境请忽略此步骤并自行处理

```shell
vim ~/.bashrc
alias python='/usr/local/bin/python3.9'
alias python3='/usr/local/bin/python3.9'
alias pip='/usr/local/bin/pip3.9'
alias pip3='/usr/local/bin/pip3.9'

wq保存并退出并生效配置文件
source ~/.bashrc
```

### 更新pip

```shell
pip3 install --upgrade pip
或:
python -m pip install --upgrade pip
```


