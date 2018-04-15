#### Django安装
```
x-shell
pip install Django==1.11.2
#windows平台提示错误后改成手动安装
pip install d:\Django-1.11.2.tar.gz
#linux平台一直失败,不指定却成功了
pip install Django

```

#### Django 目录结构

```   
Project_name 项目名称
    ---Project_name 与项目名称同名的文件夹为项目配置文件夹，放置默认配置
        ---settings.py        # 配置
        ---urls.py            # 路由系统
        ---wsgi.py            # wsgi接口
    ---app1_name              # app1文件夹,放置app1下的内容
        ---migrations         # 放置生成的数据库操作脚本
        ---admin.py           # 后台管理系统配置文件
        ---apps.py
        ---models.py          # 数据库类模型
        ---tests.py           # 单元测试
        ---views.py            # 视图层：放置python函数脚本
        ---static             # 放置静态资源：css\js\sp        
    ---app2_name              # app2文件夹,放置app2下的内容
    ---templates              # 放置html文件，html或者tml
    ---static                 # 公用的静态资源
        ---config             # 配置文件
        ---css                # css样式文件
        ---js                 # js脚本
        ---sp                 # sp
    ---manage.py              # 启动django程序
    
```

#### 路由系统 urls
    1. 静态路由 url(r'^index/', views.index), # 静态用views.index函数匹配index
    2. 动态路由
        1. url(r'^AssForHR/$',views.index), # 动态用views.index函数匹配所有一级路由为AssForHR的地址
        2. url(r'^news/(\d+)', views.news), # 动态用views.news函数匹配news/任意数字的地址
        3. url(r'^news/(?P<n1>\d+)/(?P<n1>\d+)', views.news), #动态用views.news函数匹配news/任意数字/任意数字的地址
    3. 二级路由:主目录下的urls包含了app下urls
        ```
        app01
            ---urls.py
        ```
        - project_name url: url(r'^app01/$', include("app01.urls"))