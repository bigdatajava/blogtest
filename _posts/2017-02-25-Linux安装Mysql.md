---
layout:     post
title:      "linux安装MySQL"
date:       2017-02-25
author:     "刘自超"
categories:	数据库
tags:	MySQL
---


* content
{:toc}


# linux安装MySQL

## 1. 自定义MySQL安装版本

MySQL服务器和其他所需组件的安装和升级，都来自您在安装配置包期间选择的主要版本的发行版系列。但是，您可以通过重新配置已安装的配置包，随时切换到另一个受支持的主要版本系列

> sudo dpkg-reconfigure mysql-apt-config

然后会出现一个对话框，要求您选择所需的主要版本。做出选择并选择**确定**。返回到命令提示符后，使用以下命令从MySQL APT存储库更新包信息

> sudo apt-get update

下次使用**apt-get install**命令时，将安装所选系列中的最新版本。

您可以使用相同的方法更改要使用MySQL APT存储库安装的任何其他MySQL组件的版本。



## 2. apt方式安装

>sudo apt-get install mysql-server



## 3. 常用命令

### 3.1 查看服务状态

> sudo service mysql status



### 3.2. 停止服务

> sudo service mysql stop



### 3.3. 启动服务

> sudo service mysql start





## 4. 设置登陆密码

### 4.1 找到[mysqld]段，并加入一行“skip-grant-tables”

> sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf 

### 4.2 登陆进去使用mysql表，修改密码

> $ mysql
>
> mysql> use mysql
>
> mysql> update mysql.user set authentication_string=password('123456') where user='root' and Host ='localhost';
>
> mysql> update user set plugin="mysql_native_password"; 
>
> mysql> flush privileges;
>
> mysql> quit;



### 4.3 回到sudo vi  /etc/mysql/mysql.conf.d/mysqld.cnf，把刚才加入的那一行“skip-grant-tables”注释或删除掉。

### 4.4 再次重启mysql服务sudo service mysql restart，使用新的密码登陆，修改成功



## 5. 开启远程登陆

1. 打开/etc/mysql/mysql.conf.d/mysqld.cnf, 注掉 "bind-address = 127.0.0.1", 

2. 重启 service mysql  restart

3. 执行: 

   ```
   GRANT ALL PRIVILEGES ON *.* TO 'USERNAME'@'%' IDENTIFIED BY 'PASSWORD' WITH GRANT OPTION;
   ```

注意: 这里的USERNAME是你的数据库账户，PASSWORD是你的数据库密码

例如: mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'root' WITH GRANT OPTION;

4. 执行: mysql> FLUSH PRIVILEGES;

5. OK
---------------------








著作权声明：本文首次发布于 [刘自超](https://liuwc.xyz)，转载请保留以上链接

