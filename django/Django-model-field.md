Django model 中的字段解释
Django 通过 models 实现数据库的创建、修改、删除等操作，本文为模型中一般常用的类型的清单，便于查询和使用：

- [https://www.cnblogs.com/kuku0223/p/7815035.html](https://www.cnblogs.com/kuku0223/p/7815035.html)


#### 可选field
- AutoField：一个自动递增的整型字段，添加记录时它会自动增长。你通常不需要直接使用这个字段；如果你不指定主键的话，系统会自动添加一个主键字段到你的model。(参阅自动主键字段)
- BooleanField： 布尔字段,管理工具里会自动将其描述为checkbox。
- CharField：字符串字段，单行输入，用于较短的字符串，如要保存大量文本, 使用 TextField，CharField有一个必填参数：
- CharField.max_length：字符的最大长度，django会根据这个参数在数据库层和校验层限制该字段所允许的最大字符数。

- TextField：一个容量很大的文本字段， admin 管理界面用 textarea多行编辑框表示该字段数据。
- CommaSeparatedIntegerField：用于存放逗号分隔的整数值。类似 CharField，必须maxlength 参数。
- DateField：日期字段，admin 用一个文本框 <input type=”text”> 来表示该字段数据(附带一个 JavaScript 日历和一个”Today”快捷按键。有下列额外的可选参数：
 - auto_now：当对象被保存时,自动将该字段的值设置为当前时间.通常用于表示 “last-modified” 时间戳；
 - auto_now_add：当对象首次被创建时,自动将该字段的值设置为当前时间.通常用于表示对象创建时间。

- DateTimeField：类似 DateField 支持同样的附加选项。
- EmailField：一个带有检查 Email 合法性的 CharField，不接受 maxlength 参数。
- FileField：一个文件上传字段。 要求一个必须有的参数： upload_to， 一个用于保存上载文件的本地文件系统路径。 这个路径必须包含 strftime formatting， 该格式将被上载文件的 date/time 替换(so that uploaded files don’t fill up the given directory)。在一个 model 中使用 FileField 或 ImageField 需要以下步骤：在你的 settings 文件中， 定义一个完整路径给 MEDIA_ROOT 以便让 Django在此处保存上传文件。 (出于性能考虑，这些文件并不保存到数据库。) 定义 MEDIA_URL 作为该目录的公共 URL。 要确保该目录对 WEB 服务器用户帐号是可写的。在你的 model 中添加 FileField 或 ImageField， 并确保定义了 upload_to 选项，以告诉 Django 使用 MEDIA_ROOT 的哪个子目录保存上传文件。你的数据库中要保存的只是文件的路径(相对于 MEDIA_ROOT)。 出于习惯你一定很想使用 Django 提供的 get_<fieldname>_url 函数。举例来说，如果你的 ImageField 叫作 mug_shot， 你就可以在模板中以 {{ object。get_mug_shot_url }} 这样的方式得到图像的绝对路径。
- FilePathField：选择指定目录按限制规则选择文件，有三个参数可选， 其中”path”必需的，这三个参数可以同时使用， 
 - 参数描述：
  * path：必需参数，一个目录的绝对文件系统路径。 FilePathField 据此得到可选项目。 Example： “/home/images”；
  * match：可选参数， 一个正则表达式， 作为一个字符串， FilePathField 将使用它过滤文件名。 注意这个正则表达式只会应用到 base filename 而不是路径全名。 Example： “foo。*\。txt^”， 将匹配文件 foo23.txt 却不匹配 bar.txt 或 foo23.gif；
    * recursive：可选参数， 是否包括 path 下全部子目录，True 或 False，默认值为 False。

    * match 仅应用于 base filename， 而不是路径全名。 如：FilePathField(path=”/home/images”， match=”foo.*”， recursive=True)…会匹配 /home/images/foo.gif 而不匹配 /home/images/foo/bar.gif

- FloatField：浮点型字段。 必须提供两个 参数， 参数描述：
- max_digits：总位数(不包括小数点和符号)
- decimal_places：小数位数。如：要保存最大值为 999 (小数点后保存2位)，你要这样定义字段：models.FloatField(…，max_digits=5， decimal_places=2)，要保存最大值一百万(小数点后保存10位)的话，你要这样定义：models.FloatField(…，max_digits=19， decimal_places=10)

- ImageField：类似 FileField， 不过要校验上传对象是否是一个合法图片。它有两个可选参数：height_field 和 width_field，如果提供这两个参数，则图片将按提供的高度和宽度规格保存。 该字段要求 Python Imaging 库。
- IntegerField：用于保存一个整数。
- IPAddressField：一个字符串形式的 IP 地址， (如 “202.1241.30″)。
- NullBooleanField：类似 BooleanField， 不过允许 NULL 作为其中一个选项。 推荐使用这个字段而不要用 BooleanField 加 null=True 选项。 admin 用一个选择框 <select> (三个可选择的值： “Unknown”， “Yes” 和 “No” ) 来表示这种字段数据。
- PhoneNumberField：一个带有合法美国风格电话号码校验的 CharField(格式：XXX-XXX-XXXX)。
- PositiveIntegerField：类似 IntegerField， 但取值范围为非负整数（这个字段应该是允许0值的…可以理解为无符号整数）
- PositiveSmallIntegerField：
正小整型字段，类似 PositiveIntegerField， 取值范围较小(数据库相关)SlugField“Slug” 是一个报纸术语。 slug 是某个东西的小小标记(短签)， 只包含字母，数字，下划线和连字符。它们通常用于URLs。 若你使用 Django 开发版本，你可以指定 maxlength。 若maxlength 未指定， Django 会使用默认长度： 50，它接受一个额外的参数：

- prepopulate_from: 来源于slug的自动预置列表

- SlugField：是一个报纸术语. slug 是某个东西的小小标记(短签), 只包含字母,数字,下划线和连字符.它们通常用于URLs。
- SmallIntegerField：类似 IntegerField， 不过只允许某个取值范围内的整数。(依赖数据库)
- TimeField：时间字段，类似于 DateField 和 DateTimeField。
- URLField：用于保存 URL。 若 verify_exists 参数为 True (默认)， 给定的 URL 会预先检查是否存在(即URL是否被有效装入且没有返回404响应)。
- USStateField：美国州名缩写，由两个字母组成（天朝人民无视）。
- XMLField：XML字符字段，校验值是否为合法XML的 TextField，必须提供参数：
- schema_path：校验文本的 RelaxNG schema 的文件系统路径。

#### 附：Field 选项
- null ：缺省设置为false.通常不将其用于字符型字段上，比如CharField,TextField上.字符型字段如果没有值会返回空字符串。
- blank：该字段是否可以为空。如果为假，则必须有值
- choices：一个用来选择值的2维元组。第一个值是实际存储的值，第二个用来方便进行选择。如SEX_CHOICES= ((‘F’,'Female’),(‘M’,'Male’),)
- core：db_column，db_index 如果为真将为此字段创建索引
- default：设定缺省值
- editable：如果为假，admin模式下将不能改写。缺省为真
- help_text：admin模式下帮助文档
- primary_key：设置主键，如果没有设置django创建表时会自动加上：
  - 1	id = meta.AutoField('ID', primary_key=True)
  - 2	primary_key=True implies blank=False, null=False and unique=True. Only one primary key is allowed on an object.
- radio_admin：用于admin模式下将select转换为radio显示。只用于ForeignKey或者设置了choices
unique：数据唯一
unique_for_date：日期唯一，如下例中系统将不允许title和pub_date两个都相同的数据重复出现
title = meta.CharField(maxlength=30,unique_for_date=’pub_date’)
unique_for_month / unique_for_year：用法同上
validator_list：有效性检查。非有效产生 django.core.validators.ValidationError 错误