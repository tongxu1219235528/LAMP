# LAMP
本文介绍如何在Ubuntu:16.04中搭建LAMP（Linux Apache MySQL PHP）开发环境
## 整体流程
* 安装Apache2
* 安装php5
* 安装mysql-server
* 安装php5-mysql
* 安装php5-gd
* 安装MySQL图形管理工具WorkBench 

## 安装过程及详解
### Apache2  
  * 运行命令：  
   ```$ sudo apt-get update```  
   ```$ sudo apt-get install apache2```  

  * 验证是否成功：    
   ```$ sudo apache2 -v```   

        Server version: Apache/2.4.18 (Ubuntu)    
        Server built:   2016-07-14T12:32:26

    如果显示以上以上信息则表明安装成功.
  * 更改默认目录（非必须）  
   ```$ sudo vim /etc/apache2/apache2.conf``` 

         将 "Directory /var/www/"  
         改成 "Directory '你的目录' "  
         可以将/var/www 中的默认网页复制到"你的目录"中 
   ```$ sudo vim /etc/apache2/sites-available/000-default.conf```    
          
          将 "DocumentRoot /var/www/html"  
          改成 DocumentRoot '你的目录' "  
          
   ```$ sudo /etc/init.d/apache2 restart``` 

### MySQL  
   * 运行命令：  
   ```$ sudo apt-get install mysql-server```  
   期间要输入root密码

### php7.0
   * 运行命令：  
   ```$ sudo apt-get install php7.0```   
   ubuntu16.04中不php支持php5 ,直接装包php7.0
   ```$ sudo apt-get install libapache2-mod-php7.0 ```  
   配置Apache2php+php7的  
   ```$ sudo apt-get install php7.0-mysql```    
   配置MySQL+php7的  
   ```$ sudo apt-get install php-gd```  
   * 验证php7是否安装成功:  
   ```$ php7.0 -v ```   

        PHP 7.0.8-0ubuntu0.16.04.2 (cli) ( NTS )  
        Copyright (c) 1997-2016 The PHP Group 
        Zend Engine v3.0.0, Copyright (c) 1998-2016 Zend Technologies ```   
           with Zend OPcache v7.0.8-0ubuntu0.16.04.2, Copyright (c) 1999-2016, by Zend Technologies  
     如过出现以上信息则安装成功
     
## 环境验证  
 * 我们来写一个php脚本测试是否apache可以解析php文件：新建一个php文件，phpinfo.php    
 ```$ sudo vim /var/www/html/phpinfo.php```  
   注意：如果修改了默认目录，要换成修改后的目录。  
 * 输入代码：   
  ```<?php  echo phpinfo(); ?> ```  
 * 使用浏览器访问：
  ```https://localhost/phpinfo.php```

