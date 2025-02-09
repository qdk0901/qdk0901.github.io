---
title: django笔记
description:
categories:
 - tutorial
tags:
---

- 安装  
  `pip install django`  
  `pip install django-simpleui`
  `pip install mysqlclient`

- 创建项目  
  `django-admin startproject project1`

- 创建app  
  `cd project1`  
  `django-admin startapp app1`  
  `django-admin startapp app2`

- 创建迁移  
  `python manage.py makemigrations`  
  `python manage.py migrate`

- 设置超级用户, 启用admin面板  
  `python manage.py createsuperuser`