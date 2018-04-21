## 1. 单独建类：forms
```
# 示例：类文件建在AssForHR项目下views目录下spacegame目录下，文件名为spacegame_forms
from django import forms # 从django导入forms


# 新建form表单类，用于操作表单
class _MainBuilding(forms.Form):
    building_model_id = forms.CharField(max_length=40)

```

## 2. 在view中调用form类
```
# 示例：在view中的area_main_building_edit函数中调用form类
from AssForHR.views.spacegame import spacegame_forms #从项目文件中导入定义好的表单类


# 在视图中调用form表单类
def area_main_building_edit(request, starid, areaid, panelid):
    main_building = spacegame_forms._MainBuilding() # 调用
    context = {'main_building': main_building} # 作为对象传入content
    return render(request, 'spacegame/area_main_building_edit.html', context)
```

## 3. 在前端html页面用调用form表单类并进行展示
```
{%  load staticfiles %}


<form id="add_main_building" action="" method="POST">{% csrf_token %}
{{ main_building.building_model_id }}
<button class="btn btn-primary" type="submit" value="{{ building_model.building_model_id }}">选择建造</button>
</form>
```

## 4. 在view中接收前端页面传回的post数据并进行处理
```
# 示例：在view中的area_main_building_edit函数中调用form类
from AssForHR.views.spacegame import spacegame_forms #从项目文件中导入定义好的表单类


def area_main_building_edit(request, starid, areaid, panelid):
    if request.method == "POST":
        print(request.POST)
        main_building = spacegame_forms._MainBuilding(request.POST) #POST的时候把POST结果传给表单
        if main_building.is_valid():
            print('form is ok')
        else:
            print('form is error')
            
    else:
        main_building = spacegame_forms._MainBuilding()
        
    context = {'starid': id, 'areaid': areaid, 'panelid': panelid, 'building': building
        ,'building_models': building_models,'main_building': main_building}
    return render(request, 'spacegame/area_main_building_edit.html', context)
```

## 注意：
1. 前端html的form表单用POST方法提交的时候，form的后面必须加{% csrf_token %}
```
<form id="add_main_building" action="" method="POST">{% csrf_token %}
```