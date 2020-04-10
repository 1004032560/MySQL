## 1、`LOCK TABLES`

`LOCK TABLES` 可以锁定用于当前线程的表。如果表被其他线程锁定，则当前线程会等待，直到可以获取所有锁定为止。

`UNLOCK TABLES` 可以释放当前线程获得的任何锁定。当前线程执行另一个 `LOCK TABLES` 时，或当服务器的连接被关闭时，所有由当前线程锁定的表被隐含地解锁。

具体语法如下：

~~~mysql
LOCK TABLES

	table_name [AS alias] {READ [LOCK] | [LOW_PRIORITY] WRITE}

UNLOCK TABLES
~~~



•    注意：`LOCK TABLES` 和 `UNLOCK TABLES` 有时也写为 `LOCK TABLE` 和 `UNLOCK TABLE`，两种写法含义一样。

~~~mysql
#打开两个连接MySQL数据客户端
#客户端1:
lock table teacher read;

#客户端2:查询
select * from teacher;
#--操作成功
#客户端2:更新
update teacher set salary=1000 where tid=1001;
#--等待操作！！！

#直到表释放锁
#客户端1:
unlock tables;
#客户端2:更新
update teacher set salary=1000 where tid=1001;--成功操作！！！
~~~

