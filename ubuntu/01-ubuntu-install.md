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