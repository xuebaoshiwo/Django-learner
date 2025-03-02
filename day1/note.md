# DAY1 Django 入门
## 创建Django项目
使用命令行创建Django项目：
```bash
  django-admin startproject project_name
```
Django 项目的结构和作用：
```text
myproject/
├── manage.py          # 项目的管理脚本
└── myproject/         # 项目的核心目录（与项目同名）
    ├── __init__.py    # 标识这是一个 Python 包
    ├── settings.py    # 项目的配置文件
    ├── urls.py        # URL 路由配置
    ├── asgi.py        # ASGI 配置（用于异步部署）
    └── wsgi.py        # WSGI 配置（用于同步部署）
```
在这个Django项目中创建一个应用程序app（可以理解成一个业务）：
```bash
    django-admin startapp app_name
```
Django应用程序app的项目结构：
```text
blog/
├── migrations/       # 数据库迁移文件
│   └── __init__.py
├── admin.py          # Django Admin 配置
├── apps.py           # 应用配置
├── models.py         # 数据模型
├── tests.py          # 测试代码
├── views.py          # 视图函数（业务逻辑代码）
└── __init__.py       # 标识这是一个 Python 包
```
## 完成第一次Django请求
首先要在myproject/urls.py中绑定路由：
```python
from django.contrib import admin
from django.urls import path
from app1.views import test1

urlpatterns = [
    path("admin/", admin.site.urls),
    path("/app1/test", test1)
]
```
test1定义在/app1/views.py中：
```python
from django.shortcuts import render, HttpResponse


# Create your views here.
def test1(request):
    print("test1 成功")
    return HttpResponse("Success")
```
启动程序
```bash
    python manage.py runserver localhost:8000
```