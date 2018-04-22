## 腾讯云ubuntu环境重装

### 1. 环境重装

### 2. 安装gnome桌面
```
# 进入命令行环境
$ sudo apt-get update
# 安装gnome
$ sudo apt-get install gnome-session-flashback
```

### 3. 重启设备
```
# 现在立即重启
$sudo shutdown -r now 
```

### 4. XAMPP安装
```
# 下载xampp:从官网复制lampp下载地址付在-c后面
$wget -c https://downloadsapachefriends.global.ssl.fastly.net/xampp-files/7.2.4/xampp-linux-x64-7.2.4-0-installer.run
# 给.run文件权限,跳转到下载的目录下
$chmod 777 ./xampp-linux-x64-7.2.4-0-installer.run
# 安装xampp
$./xampp-linux-x64-7.2.4-0-installer.run
# 经过配置后默认后安装到opt/lampp
```

### 5. pip安装
- pip用于安装python相关的包，注意安装支持python3的pip
```
$apt install python3-pip
```

### 6. mysql client安装
 apt-get install mysql-client-core-5.7


### 7. UBUNTU16-XAMPP-MYSQL登录

```
ubuntu 16环境下，xshell5命令行环境中，通过xampp安装的mysql 到当前目录下启动
# /opt/lampp/bin/mysql -uroot -p*********
提示如下表示登录成功
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 128
Server version: 10.1.21-MariaDB Source distribution
Copyright (c) 2000, 2016, Oracle, MariaDB Corporation Ab and others.
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
MariaDB [(none)]>
```

### 8. Database operate
```
创建全局用户
CREATE USER 'pig'@'%' IDENTIFIED BY '123456';
授权us
GRANT ALL ON *.* TO 'pig'@'%';

### 9. 创建数据库
```
create database assforgaia default charset utf8;
```

### 10. 安装django
```
pip3 install Django==2.0.4
```

安装git
apt-get install git

定位到目录下
cd /peter/work/
初始化仓库
git init
复制代码
git pull https://github.com/15011283031/HRAC.git
待处理 切换分支

更新ubuntu默认的编译器到python3
sudo update-alternatives --install /usr/bin/python python /usr/bin/python2 100
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 150

原因是 没有安装:libmysqlclient-dev
$ sudo apt-get install libmysqlclient-dev

pip3 install mysqlclient

sudo pip3 install pycrypto

pip3 install suds-jurko

git clone只能clone远程库的master分支，无法clone所有分支，解决办法如下：
1. 找一个干净目录，假设是git_work
2. cd git_work
3. git clone http://myrepo.xxx.com/project/.git ,这样在git_work目录下得到一个project子目录
4. cd project
5. git branch -a，列出所有分支名称如下：
remotes/origin/dev
remotes/origin/release
6. git checkout -b dev origin/dev，作用是checkout远程的dev分支，在本地起名为dev分支，并切换到本地的dev分支
7. git checkout -b release origin/release，作用参见上一步解释
8. git checkout dev，切换回dev分支，并开始开发。


pip3 install 