# Task00/01: 数据库环境搭建及初步了解

## Task00: 绪论 - 环境搭建

### 1. MySQL 8.0 安装

| MySQL 8.0社区版的安装 | Windows                                                      | Mac                                                          | Linux - Centos                                               |
| --------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 安装                  | **官网：**https://dev.mysql.com/downloads/<br/>* 最新版本：[MySQL Installer for Windows](https://dev.mysql.com/downloads/installer/)<br/>* 历史版本：[Download Archives 2](https://downloads.mysql.com/archives/) -> [MySQL Installer](https://downloads.mysql.com/archives/installer/)<br/>**百度网盘：**<br/>* 下载链接：[https://pan.baidu.com/s/1SOtMoVqqRXwa2qD0siHcIg 9](https://pan.baidu.com/s/1SOtMoVqqRXwa2qD0siHcIg)提取码：80lf <br/>* 备用下载链接：https://pan.baidu.com/s/1zK2vj50DvuAee-EqAcl-0A提取码：80lf | **官网：**https://dev.mysql.com/downloads/<br/>* 最新版本：[MySQL Community Server](https://dev.mysql.com/downloads/mysql/) -> macOS<br/>* 历史版本：[Download Archives 2](https://downloads.mysql.com/archives/)https://downloads.mysql.com/archives/) -> [MySQL Installer](https://downloads.mysql.com/archives/installer/)<br/>**百度网盘：**<br/>* 下载链接：[https://pan.baidu.com/s/1ka22UtzqFdOaIosrpKz92w 1](https://pan.baidu.com/s/1ka22UtzqFdOaIosrpKz92w)提取码: 8xh4 <br/>* 备用下载链接：[https://pan.baidu.com/s/1XeA_8PQvvRePEdZ5ayOT-Q 1](https://pan.baidu.com/s/1XeA_8PQvvRePEdZ5ayOT-Q)提取码：8xh4 | * 下载：</br>`wget https://dev.mysql.com/get/mysql80-community-release-el7-2.noarch.rpm`</br>* 用yum命令安装下载好的rpm包：</br>`yum -y install mysql80-community-release-el7-2.noarch.rpm`</br> * 安装MySQL服务器：`yum -y install mysql-community-server` |
| 安装/启动关键信息     | * Choosing a Setup Type: Full(完全安装模式)<br/>*  High Availability: Standalone MySQL Server/Classic MySQL Replication</br>* Type and Networking: ☑️Show Advanced and Logging Options</br> * Authentication Method: Use Legacy Authentication Method (Retain MySQL 5.x Compatibility)</br> * Advanced Options: Lower Case (default) | * 简单密码，如果强密码，截图保存</br>* 安装完成后，电脑系统偏好设置中会出现MySQL的服务标识</br> * 环境变量配置：`PATH="$PATH":/usr/local/mysql/bin`</br>`export PATH=$PATH:/usr/local/mysql/bin`</br>`source ~/.bash_profile`</br> * 终端登录MySQL: `mysql -u root -p` | * 启动 MySQL: </br>`systemctl start  mysqld.service`</br> * 查看MySQL状态: <br>`systemctl status mysqld.service`</br> * 重新启动 Mysql 和停止 Mysql 的命令如下：</br>`service mysqld restart  #重新启动 Mysql systemctl stop mysqld.service   #停止 Mysql`</br>* 查看临时密码:</br>`grep 'temporary password' /var/log/mysqld.log`</br>* 登录 |

### 2. MySQL的连接

| 命令行                                          | 图形界面                                                     |
| ----------------------------------------------- | ------------------------------------------------------------ |
| **Windows:**</br> MySQL 8.0 Command Line Client | * [MySQL Workbench](https://dev.mysql.com/downloads/workbench/) - Windows/macOS/Linux</br> * [HeidiSQL](https://www.heidisql.com/download.php 2) - Linux</br> * [DBeaver](https://dbeaver.io/) - Windows/macOS/Linux</br> * Navicat </br>* [SQLyog](https://github.com/webyog/sqlyog-community/wiki/Downloads 2) </br> * DataGrip- Windows/macOS/Linux |

### Task01: 初识数据库

| 基础知识                                                     | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 数据库（Database，DB）                                       | 将大量数据保存起来，通过计算机加工而成的可以进行高效访问的数据集合 |
| 数据库管理系统（Database Management System，DBMS）           | 用来管理数据库的计算机系统                                   |
| DBMS的种类                                                   | DBMS 主要通过数据的保存格式（数据库的种类）来进行分类：<br> * 层次数据库（Hierarchical Database，HDB）</br>* 关系数据库（Relational Database，RDB）</br>* 面向对象数据库（Object Oriented Database，OODB）</br> * XML数据库（XML Database，XMLDB）</br> * 键值存储系统（Key-Value Store，KVS） |
| 关系数据库管理系统（Relational Database Management System，RDBMS） | * Oracle Database：甲骨文公司的RDBMS </br>* SQL Server：微软公司的RDBMS </br>* DB2：IBM公司的RDBMS </br>* PostgreSQL：开源的RDBMS </br>* MySQL：开源的RDBMS |
| RDBMS的常见系统结构                                          | 最常用的系统结构就是客户端 / 服务器类型（C/S类型）这种结构</br>![](/Users/heyujiang/unknown/学习输出/DatawhaleLearning_SQL/Task00:01_数据库环境搭建及初步了解/1.jpeg) |
| 表结构                                                       | * **列名**：数据的项目名称</br> * **行/记录**：一条记录 </br> * **列/字段**：表中存储的数据项目</br> * **单元格**：行和列交汇的地方称为单元格，一个单元格中只能输入一条记录 |
| SQL语句                                                      | * DDL（Data Definition Language，数据定义语言） 用来创建或者删除存储数据用的数据库以及数据库中的表等对象</br>&emsp;** CREATE: 创建数据库和表等对象</br> &emsp;** DROP: 删除数据库和表等对象</br> &emsp; ** ALTER ： 修改数据库和表等对象的结构 </br> * DML（Data Manipulation Language，数据操纵语言） 用来查询或者变更表中的记录 </br>  &emsp; ** SELECT ：查询表中的数据</br>  &emsp; ** INSERT ：向表中插入新数据</br> &emsp;** UPDATE ：更新表中的数据</br> &emsp; ** DELETE ：删除表中的数据</br> |
|                                                              |                                                              |
|                                                              |                                                              |

