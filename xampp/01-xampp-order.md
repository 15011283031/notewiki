## 2.1. XAMPP的安装及部署

### 2.1.1. XAMPP安装
1. 在网站上下载XAMPP For linux 64bit

![img](170408_101601_000001)

2. 通过x-ftp将下载好的xampp传至/home/ubuntu/Downloads下

![img](170408_101601_000002.png)

3. 登录root账户
```
ubuntu@ubuntu:~$ su
Password: 
```
4. 安装XAMPP
```
$ chmod +x /home/ubuntu/Downloads/xampp-linux-x64-7.1.1-0-installer.run
root@ubuntu:/home/ubuntu# /home/ubuntu/Downloads/xampp-linux-x64-7.1.1-0-installer.run
```

### 2.1.2. XAMPP桌面版本的启动
```
$sudo /opt/lampp/manageer-linux-x64.run
```
1. 启动xampp后，启动mysql后，就可以通过在浏览器中输入http://localhost/phpmyadmin来访问pypmyadmin来管理mysql数据库
2. 注意变更默认站点发布地址后，xampp默认安装的phpmyadmin可能会失效

### 2.1.3. XAMPP下站点的部署及配置

#### 2.1.3.1. wordpress站点部署
3. 通过ftp传输wordpress到/home/ubuntu/Downloads
4. 移动wordpress到部署站点下/opt/lampp/htdocs

```
ubuntu@ubuntu:~$ su
Password: 
# cp -r /home/ubuntu/Downloads/wordpress /opt/lampp/htdocs/wordpress
```
5. 配置wordpress config文件中设置数据库连接账户密码
```
# vim /opt/lampp/htdocs/wordpress/wp-config.php
```

### 2.1.3. XAMPP操作
```
启动 XAMPP
/opt/lampp/./lampp start
停止 XAMPP
/opt/lampp/./lampp stop
重启 XAMPP
/opt/lampp/lampp restart
安全设置
/opt/lampp/./lampp security
卸载 XAMPP
rm -rf /opt/lampp
```