---
title: gva自动代码笔记
description:
categories:
 - tutorial
tags:
---
使用gva后台新建pkgTest package, 并根据数据库的test表生成代码后, git diff查看自动添加了哪些代码  
- server/api/v1 目录, 添加了pkgTest目录, 增加了下面的文件 
  - enter.go, 创建了pkgTest对应的ApiGroup
![alt text](/assets/images/image.png)  
  - test_.go, 对应的是test表的增删查改操作, 这里是做一些必要处理, 检查request里的参数后, 调用service目录下对应的接口
![alt text](/assets/images/image-1.png)

- server/initialize/gorm_biz.go 文件, 增加test表的AutoMigrate操作
![alt text](/assets/images/image-2.png)

- server/initialize/router_biz.go 文件, 增加pkgTest对应的路由
![alt text](/assets/images/image-3.png)

- server/model 目录, 添加了pkgTest目录, 增加了下面的文件
  - request/test_.go, 这里是TestSearch结构
  ![alt text](/assets/images/image-4.png)

  - test_.go, 这里是test表对应的golang结构
  ![alt text](/assets/images/image-5.png)

- server/router 目录, 添加了pkgTest目录, 增加了下面的文件
  - enter.go, 创建了pkgTest对应的RouterGroup
  ![alt text](/assets/images/image-6.png)

  - test_.go, 这里创建了pkgTest相关路由, 路由到pkgTest增删查改api的实现
  ![alt text](/assets/images/image-7.png)

- server/router/enter.go 文件, 将上面的pkgTest RouterGroup注册进上级路由
![alt text](/assets/images/image-8.png)

- server/service 目录, 添加了pkgTest目录, 增加了下面的文件
  - enter.go, 创建了pkgTest对应的ServiceGroup
  ![alt text](/assets/images/image-9.png)

  - test_.go, 对test表操作, 实现了具体的增删查改操作
  ![alt text](/images/image-10.png)

- server/service/enter.go 文件, 将上面创建的ServiceGroup注册进上级服务组
![alt text](/assets/images/image-11.png)

- web/src/api/ 目录, 增加了pkgTest目录, 包含下面文件
  - test.js, 实现对后端的增删查改请求
  ![alt text](/assets/images/image-12.png)

- web/src/view/ 目录, 增加了pkgTest目录, 包含下面文件
  - test.vue, 实现了前端的test表查看页面
  - testForm.vue, 存疑
