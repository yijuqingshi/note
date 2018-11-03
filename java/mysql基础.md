# Mysql数据库基础


## Mysql基本命令
```
  mysql -h 192.168.0.200 -u root -p  //登陆数据库

  show databases; //显示所有数据库

  use vcoindb; //使用数据库

  create database 数据名称; //create database test;

  create database 数据库名称 character set 编码 collate 校对规则;

  create database test character set "utf8"  collate "utf8_bin"

  drop database test //删除数据库

  alter database test character set "gbk"  //修改编码

  show tables; //查看数据库所有表

  show columns from user; //查看user表的列信息

```

## CURD语句（增删改查）

* 创建表

```
create table 表名(

    字段名 类型(长度) 约束,
    字段名 类型(长度) 约束,
    字段名 类型(长度) 约束
  );

  注意：表名后跟着小括号并且带分号，类型一般有默认长度，但是字符串必须指明长度，int类默认11

  实例：
  create table user(
      id int not null auto_increment ,
      name varchar(20),
      password varchar(40),
      age int,
      reg_time datetime,
      primary key (id)
    );
```
