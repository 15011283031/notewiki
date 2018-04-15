### Django

#### models 外键关联处理
```
class BuildingLists(models.Model):
    BuildingID = models.CharField(max_length=40, default='0')
    OwnerID = models.CharField(max_length=200, default='undifined')
    BuildingStatusID = models.CharField(max_length=200, default='undifined')
    PlayerID = models.ForeignKey(to="PlayerLists", to_field='PlayerID', **on_delete=models.CASCADE, default='0'**)
# 作为外键时 必须有删除条件和默认值

    def __str__(self):
        return '||BuildingID:%s | OwnerID:%s| BuildingStatusID:%s||' \
               % (self.BuildingID, self.OwnerID, self.BuildingStatusID)


class PlayerLists(models.Model):
    PlayerID = models.CharField(max_length=40, default='0', **unique=True**, null=False)
# unique=True 作为外键时必须唯一
    Name = models.CharField(max_length=200, default='undifined')
    CreateTime = models.DateTimeField(auto_now_add=True)

```


####django orm示例
```
class Business(models.Model):
    # id
    caption = models.CharField(max_length=32)
    code = models.CharField(max_length=32,null=True,default="SA")
    # 新增列 允许为空null=True 或 default="SA"，就不会提示信息

class Host(models.Model):
    nid = models.AutoField(primary_key=True)
    hostname = models.CharField(max_length=32,db_index=True)  # 加上索引
    ip = models.GenericIPAddressField(protocol="ipv4",db_index=True)
    port = models.IntegerField()
    b = models.ForeignKey(to="Business", to_field='id')  # 表中生成列名：b_id
    # b = models.ForeignKey("Business", to_field='id')   # 外键约束，
    # b = models.ForeignKey("Business")   #只写表名，默认与那张表主键关联

# 外键：
#   v = models.Host.objects.filter(nid__gt=0)
#   v[0].b.caption  #---->  通过.进行跨表
```



#### 字段属性

- 创建时间
    - CreateTime = models.DateTimeField(auto_now_add=True)
    - anto_now_add 新增时自动创建时间
    - auto_now 更新时自动创建时间

#### 数据库orm操作 增删改查
```
# 增
models.User.objects.create(name='qianxiaohu',age=18) # 第一种
dic = {'name': 'xx', 'age': 19}                      # 第二种
models.User.objects.create(**dic)    # **dic
obj = models.User(name='xiao',age=18)                # 第三种
# 第四种
dic = {"username":'eric',"password":'123'}
models.UserInfo.objects.create(**dic)

obj.save()
# 删
models.User.objects.filter(id=1).delete()
models.UserInfo.obejcts.filter(username='alex').delete()
# 改
models.User.objects.filter(id__gt=1).update(name='alex',age=84)
models.UserInfo.objects.all().update(age=18)
dic = {'name': 'xx', 'age': 19}
models.User.objects.filter(id__gt=1).update(**dic)
# 查
models.User.objects.filter(id=1,name='root')
models.User.objects.filter(id__gt=1,name='root')# 大于
models.User.objects.filter(id__lt=1)            # 小于
models.User.objects.filter(id__gte=1)           # 大于等于
models.User.objects.filter(id__lte=1)           # 小于等于
models.User.objects.all()
models.User.objects.last()
models.UserInfo.objects.filter(age=18)
models.UserInfo.objects.filter(age=18).first()

models.User.objects.filter(id=1,name='root')
dic = {'name': 'xx', 'age__gt': 19}
models.User.objects.filter(**dic)  # 这里也可以传字典，增删改查都可以加字典
```   



#### 数据库操作

##### 创建类
```
class EX_SourceSetting(models.Model):
    model_name = models.CharField(max_length=40)
    source_table_name = models.CharField(max_length=40)
    source_col_name = models.CharField(max_length=40)
    source_version_name = models.CharField(max_length=40)
```

##### 使用命令根据类创建表
        - python manage.py makemigrations # 生成配置文件
        - python manage.py migrate       # 根据配置文件创建数据库相关


##### 当需要进行POST操作时需要关闭该安全规则
```
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    # 'django.middleware.csrf.CsrfViewMiddleware',  # 当需要post传递数据时需要关闭该安全规则
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]
```

#### 外部Python文件调用django mode
1. 需要首先配置django的默认app以及设置
    - import os, django
    - os.environ['DJANGO_SETTINGS_MODULE'] ='HRA.settings'
2. 然后启动django
    - django.setup() 



#### Django配置
1. 创建项目
```
在CMD\Prompt，linux shell中都可以执行
1 定位到需要创建项目的目录
cd /home/ubuntu/HumanResourcesAss
2 创建Django项目
django-admin.py startproject AssForGaia_Web
3 创建app
python manage.py startapp myapp_name
4 将app 插入项目
在 settrings.py 中增加 myapp_name
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'myapp_name',
]

```
2. 启动项目
```
1. 进入项目(项目名称路径)
cd ./AssForGaia_Web
2. 启动配置
python manage.py migrate
3. 启动项目
Python manage.py runserver 0.0.0.0:8000
```
> 启动后windows可以通过http://127.0.0.1:8000/来访问查看

3. 外网访问环境的设定
```
1. 在settings.py中设定all_hosts(在当前目录的下一层)
vim ./AssForGaia_Web/settings.py
2. 在ALLOWED_HOSTS中添加地址，比如外网服务器就是www.hr-a.info
ALLOWED_HOSTS = ["127.0.0.1","Peter"]
注意有的局域网会对域名解析进行控制，所以必须使用IP地址访问才能保证速度
3. 保存文件，重新启动项目

```
4. 项目简介
    - 第二层的项目名称为根目录 .
    - 第二层导入的时候可以用 from . import view
5. url() 路由系统函数
    - regex: 正则表达式，与之匹配的 URL 会执行对应的第二个参数 view。
        - 示例：r'^hello$'；
        - 示例2：url(r'^news/(\d+)',views.news), (\d+)表示正则匹配任意1个数字，一个正则在后台用一个参数接收
        - 示例3：url(r'^news/(?P<n1>\d+)/(?P<n2>\d+)', views.news), ?P表示参数；n1、n2是参数名称；\d+是正则匹配任意数值，接收时使用n1\n2这样的形参对应调用即可。
            - views 中可写：def news(request,n1,n2)
    - view: 用于执行与正则表达式匹配的 URL 请求。示例：view.hello
    - kwargs: 视图使用的字典类型的参数。
    - name: 用来反向获取 URL。


#### Django 依赖数据库
    - 数据库配置在 settings 中
    - 生成数据库表的操作
        - python manage.py makemirations # 生成配置文件
        - python manage.py migrate       # 根据配置文件创建数据库相关


#### Django admin 后台启动
1. python manage.py createsuperuser      # 创建超级用户
2. http://127.0.0.1:8000/admin/          # 可用于操作数据库等

#### 本机登录MYSQL
- 如果mysql不是默认安装在C盘，需要先定位到bin文件
- 默认密码是1qaz2wsx
```
 CMD
 CD e:\soft\xampp\mysql\bin
 mysql -hlocalhost -uroot -p
 1qaz2wsx
```

#### Django 创建mysql 数据库连接
1. 导出所有数据
```
#导出后再导入一直报错，还未处理
python manage.py dumpdata > mysite_all_data.json
```
2. 登录MYSQL数据库
```
 CMD
 CD e:\soft\xampp\mysql\bin
 mysql -hlocalhost -uroot -p
 1qaz2wsx
```
3. show databases 查看已有数据库
```
show databases 
```
4. 创建UTF-8格式的数据库 AssForGaia
```
CREATE DATABASE `AssForGaia` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
```
5. 创建新用户
```
#linux区分大小写，注意数据库名称
grant all privileges on assforgaia.* to "AssForGaia"@localhost identified by "1qaz2wsx";
```
6. 刷新权限
```
flush privileges;
```
7. 退出数据库shell
```
exit;
```
8. 配置django settings中关于databases字典
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'AssForGaia',
        'USER': 'assforgaia',
        'PASSWORD':'1qaz2wsx',
        'HOST':'localhost',
        'PORT':'3306',
    }
}
```
```linux下
$ cd /home/ubuntu/HumanResourcesAss/AssForGaia_Web
$ sudo chmod 777 ./AssForGaia_Web/settings.py
$ vim ./AssForGaia_Web/settings.py
配置同上
$ sudo chmod 755 ./AssForGaia_Web/settings.py
```

9. 安装mysqlclient support python 3.x
```
pip install mysqlclient
```
```
ubuntu 下安装
$ pip install mysqlclient
提示错误 mysql_config not found
原因是 没有安装:libmysqlclient-dev
$ sudo apt-get install libmysqlclient-dev
然后 找到mysql_config文件的路径 第一行输完继续第二行 然后等待，会有文件列表出来
$ sudo updatedb
locate mysql_config
查看到 mysql_config的位置为：/usr/bin/mysql_config
将 mysqlclient 源码包 .tar.gz 下载到本地，打开，找到 setup_posix.py 文件
在文件中找到 mysql_config.path 将设定值 =['mysql_config'] 改成 =['/usr/bin/mysql_config']
重新打包上传到服务器，使用su登录root账户安装
$ pip install /home/ubuntu/Downloads/mysqlclient-1.3.10.tar.gz
```
10. 重新配置数据库
```
# cd /home/ubuntu/HumanResourcesAss/AssForGaia_Web
# python manage.py migrate
```
    - 报错提示Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'
    - 原因是由于lampp 安装 mysql 后 mysql 不是在默认目录下 而是在lampp 下
    - 需要创建软连接，将默认目录与实际目录链接
```
$ sudo ln -s /opt/lampp/var/mysql/mysql.sock /var/run/mysqld/mysqld.sock
mysqld.sock 的父目录不存在时会提示no such file or path，需要先创建父目录
$ mkdir -p /var/run/mysqld/