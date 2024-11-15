---
title: mysql安装
description:
categories:
 - tutorial
tags:
---

安装mysql
```
apt remove --purge *mysql*  
rm -rf /etc/mysql /var/lib/mysql  
apt remove --purge *mariadb*  
apt install mysql-server  
```

这时候root用户没有密码, `mysql -uroot` 进入mysql命令行界面  
设置密码  
```
alter user 'root'@'localhost' identified with mysql_native_password by 'root';
flush privileges;
```