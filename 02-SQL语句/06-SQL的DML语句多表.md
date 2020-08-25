学生`students`表：

| sid  | name | age  | sex  |
| ---- | ---- | ---- | ---- |
| 1001 | 张三 | 17   | 李四 |
|      |      |      |      |
|      |      |      |      |



课程表`courses`表：

| cid  | name |
| ---- | ---- |
|      |      |
|      |      |



设置外键约束，将多个表连接起来，创建`scores`表：

~~~mysql
create table scores(
   sid int,
   cid int,
   score int,
   #设置外键
   constraint fk_sid foreign key(sid) references students(sid),
   constraint fk_cid foreign key(cid) references courses(cid)    
)
~~~

分数`scores`表：

| sid  | cid  | score |
| ---- | ---- | ----- |
|      |      |       |
|      |      |       |
|      |      |       |



修改默认值：

~~~~mysql
alter table employees alter column employeeRole set default "common";
~~~~

删除默认值：

~~~mysql
alter table employees alter column employeeRole drop default;
~~~

修改自动增长开始的值：

~~~mysql
alter table customer alter column id  AUTO_INCREMENT=104;
~~~

修改外键：

在`Navicat`中设计外键，需要在外键栏中设计好之后，再在索引栏中，将外键名，栏位（当前表中，外键的字段），索引类型（默认`Normal`），索引方法（默认`BTREE`）。



显示学生的名字和课程编号以及分数

~~~mysql
#笛卡尔积
select * from student,scores;
~~~

笛卡尔积原本是代数的概念，他的意思是对于两个不同的集合`A, B`。

对于A中的每一个元素，都有对于在`B`中的所有元素做连接运算 。

可以见得对于两个元组分别为`m, n`的表。

笛卡尔积后得到的元组个数为`m x n`个元组。

而对于`mysql`来说，**默认的连接就是笛卡尔积连接**。



### 1、表连接

当需要同时显示多个表中的字段，可以用表连接来实现。

表连接分为内连接和外连接，它们之间最大的区别是：

内连接仅选出两张表中互相匹配的记录；

而外连接会选出其他不匹配的记录。



`inner join`内连接：

包含两个表中共同拥有的匹配的记录。

~~~mysql
select * from students inner join scores on students.sid = scores.sid;
~~~



`left join`左外连接：

`left out join`：其中`out`可以省略

包含所有的左边表中的记录甚至是右边表中没有和它匹配的记录。

~~~mysql
select * from students left join scores on students.sid = scores.sid;
~~~



`right join`右外连接：

`right out join`：其中`out`可以省略

包含所有的右边表中的记录甚至是左边表中没有和它匹配的记录。

~~~mysql
select st.id,st.name,sc.cid,sc.score  from students as st right join scores as sc on students.sid = scores.sid;
~~~



**注意：**

1、表名太长，可以给该表起一个别名，在获取该表的字段时比较方便；

~~~mysql
[表名] as [表别名]
~~~

2、在表连接中使用`on`做连接判断条件。

3、设置年龄大于20小于50：

`age int check(age>20 and age<50)`。

4、设置性别默认为男或者女：

`sex varchar(20) default '男'  check(sex='男'  or sex='女')`。



### 2、子查询

在某些情况下，当进行查询的时候，需要的条件是另外一个`select`语句的结果，这个时候，就要用到**子查询**。

用于子查询的**关键字**主要包括`in, not in, =, !=, exists, not exists`等。

~~~mysql
#子查询基本格式
Select * from [表名] where [字段] [关键字] (select语句)
~~~



### 3、记录联合

我们经常会碰到这样的应用，将两个表的数据按照一定的查询条件查询出来后，将结果合并到一起显示出来，这个时候，就需要用`union`和`union all`关键字来实现这样的功能，具体语法如下：

`SELECT * FROM t1 [UNION|UNION ALL] SELECT * FROM t2 ......`

`union`和`union all`的主要区别是`union all`是把结果集直接合并在一起，而`union`是将`union all`后的结果进行一次`DISTINCT`，去除重复记录后的结果。

注意：要求表具有相同的列结构，列数也要相同，列名可以不同，以第一个表的列名为新表的列名