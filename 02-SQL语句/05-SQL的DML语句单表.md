## 创建表，`userTable`为表名

~~~mysql
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
~~~



`userTable`表：

| id   | name  | role  | sex  | age  |
| ---- | ----- | ----- | ---- | ---- |
| 100  | smart | admin | 男   | 20   |



### 1、增加数据

~~~mysql
#增添数据的基本格式
insert into [表名] ([字段]全部字段都有时，可以省略) values(值);

#增加全部的数据时，可以省略表名后的字段，但是，values后的数据必须按照创建表时，属性的顺序输入
insert into userTable values(101,"looper","admin","女",18)
insert into userTable(id,name,role,sex,age) values(103,"camel","common","男",19)

#增加部分的数据时，必须将字段与values后的数据一一对应
insert into user(id,name,sex,age) values(103,"looper","男",19)
~~~



### 2、删除数据

~~~mysql
#删除及基本格式
delete from [表名] where [判断条件];

#删除userTable中年龄大于18并且（and）小于25的用户
delete from userTable where age>18 and age<25
#删除userTable中年龄大于18或者（or）小于25的用户
delete from userTable where age>18 or age<25
~~~



### 3、修改数据

~~~mysql
#修改的基本格式
#set之后，不加where判断条件的话，会将该字段所有的值成新值
update [表名] set [字段=新值];
#set之后，添加要修改的条件
update [表名] set [字段=新值] where [判断条件];


~~~



### 4、查找数据

~~~mysql
#查询的基本格式
select [字段] from [表名] where [判断条件];

#查询所有信息
select * from teacher
#查询某些字段的信息
select id,name,age from userTable
#查询年龄大于18的用户的id,name,role
select id,name,role from userTable where age>18
#去除查询中重复的信息
select distinct,name from userTable where age>18
~~~



* #### 排序查询

~~~mysql
#将查询的结果进行排序,使用order by
#asc:表示升序
#desc:表示降序
#默认为升序
select * from 表名 order by 字段 [asc/desc];
~~~



* #### 分页查询

~~~mysql
#将查询的结果分页显示,使用limit关键字
#offset_start:表示记录的起始偏移量 注意：索引从0开始
#row_count:表示显示的行数
select * from 表名 where 查询条件 [limit offset_start,row_count]
~~~



* #### 分组查询

聚合函数：

`sum()`求和、`count()`记录数、`avg()`平均数、`max()`最大值、`min()`最小值等。

`group by`关键字：表示要进行分类聚合的字段；

比如要按照部门分类统计员工数据，部门就应该写在`group by`后面；

`with rollup`是可选参数，表明是否对分类聚合后的结果进行再汇总；

`having`关键字：表示对分类后的结果在进行条件过滤。

~~~mysql
#分组查询的基本格式
select [字段],[聚合函数] from [表名] where[判断条件] group by [字段] having[判断条件]
~~~


