### `DCL(Data Control Language)`语句

数据控制语句，用于控制不同数据段直接的许可和访问级别的语句。这些语句定义了数据库、表、字段、用户的访问权限和安全级别。常用的语句关键字主要包括`grant`、`revoke`等。



### 1、创建新用户：

创建一个数据库用户：`looper`，密码：`123456`：

`create user 'looper'@'localhost' identified by '123456';`

注意：

用户新建也要先登录`root`用户；`Exit`是退出。



### 2、授权：

授予`looper`用户对`students`数据库中所有表的`SELECT`和`INSERT`权限：

`grant SELECT, INSERT on students.* to 'looper'@'localhost';`



### 3、撤销权限

撤销`looper`用户对`students`数据库中所有表的`SELECT`权限：

`revoke SELECT on students.* from 'looper'@'localhost';`


