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


