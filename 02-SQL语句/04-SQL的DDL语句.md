### `DOS`界面操作数据库

`cmd`进入`DOS`界面输入命令行-输入`mysql -uroot -p`

按`Enter`键之后输入密码，连接进入数据库。



#### 1、数据库操作

~~~mysql
#创建数据库,DataBaseName为数据库名：
create database DataBaseName;

#删除数据库
drop database DataBaseName;

#显示已存在的数据库
show databases;
#+--------------------+
#| Database           |
#+--------------------+
#| information_schema |
#| dome               |
#| dome2              |
#| mysql              |
#| performance_schema |
#| test               |
#+--------------------+

#切换或者使用某个数据库
use DataBaseName;
~~~



#### 2、创建表是可以对属性进行一些约束

| 名称                        | 关键字         | 说明                                                |
| --------------------------- | -------------- | --------------------------------------------------- |
| 非空约束                    | NOT NULL       | 字段不允许为空                                      |
| 默认约束                    | DEFAULT        | 赋予某字段默认值                                    |
| 唯一约束                    | UNIQUE KEY     | 设置字段的值是唯一的且允许为空，但只能有一个空值    |
| 主键约束                    | PRIMARY KEY    | 设置该字段为表的主键，可唯一标识该表记录            |
| 外键约束                    | FOREIGN KEY    | 用于在两表之间建立关系，需要指定引用主表的哪一字段  |
| 自动增长                    | AUTO_INCREMENT | 设置该列为自增字段，默认每条自增1，通常用于设置主键 |
| 检查约束（在mysql中被忽略） | CHECK          | 用于检查数据                                        |



#### 3、表操作

~~~mysql
#显示当前数据库中的所有表
show tables;
#+----------------+
#| Tables_in_dome |
#+----------------+
#| student        |
#| teacher        |
#| user           |
#+----------------+

#创建表,userTable为表名
create table userTable(
    #int类型的id,并且为主键
	id int primary key,
    #varchar类型的用户名,不能重复
    name varchar(50) UNIQUE key,
    #默认值为'common'
    role varchar(20) default 'common',
    #varchar类型,不能为空
    sex varchar(20) not null,
    #int类型的age
    age int not null
);

#删除表
drop table TableName;

#显示表的结构
desc userTable;
#+-------+-------------+------+-----+---------+-------+
#| Field | Type        | Null | Key | Default | Extra |
#+-------+-------------+------+-----+---------+-------+
#| id    | int(11)     | NO   | PRI | NULL    |       |
#| name  | varchar(50) | YES  | UNI | NULL    |       |
#| role  | varchar(50) | YES  |     | common  |       |
#| sex   | varchar(20) | NO   |     | common  |       |
#| age   | int(11)     | NO   |     | NULL    |       |
#+-------+-------------+------+-----+---------+-------+
~~~



