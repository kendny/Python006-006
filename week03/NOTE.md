学习笔记



### 相关的命令（centos）

##### 安装mysql

- 查看CPU类型

arch

- 查看系统版本信息

```shell
cat /etc/readhat-relase
```

-  查看系统安装的版本信息

```shell
rpm -qa | grep -i 'mysql'
```

- 查看mysql的随机密码

```mysql
grep 'password' /var/log/mysqld.log | head -1
```



##### sql操作密码

- 更改密码

```sql
ALTER USER 'root'@'localhost' IDENTIFIED BY 'new_pwd';

#查看密码的安全性
SHOW VARIABLES LIKE 'validate_password%';

# 设置密码策略
set global validate_password_policy = 0;
```

- 事务

查看mysql事务是否自动提交

```sql
> show variables like 'autocommit';

#关闭自动提交
> set autocommit=0;
```



参考：http://www.hellojava.com/a/92861.html

#### Mysql字符集

查看字符集：

```sql
mysql> show variables like '%character%';
```

查看校对规则

```sql
mysql> show variables like 'collation_%';
```

注意： MySQL 中的 utf8 不是 UTF-8 字符集.

> 参考：https://www.cnblogs.com/wcwen1990/p/6917109.html

- 查看表的创建规则

```sql
show create database db1; 
```





对mysql服务状态的操作

```shell
systemctl restart mysqld
systemctl status mysqld


```



### Python操作Mysql的多种方法



### 那些你需要精通的SQL知识

SQL语言功能划分：

DQL：Data Query Language，数据查询语言，开发工程师学习的重点。

DDL：Data Definition Language，数据定义语言，操作库和表结构。

DML：Data Manipulation Language，数据操作语言，操作表中记录。

DCL：Data Control Language，数据控制语言， 安全和访问权限控制。





创建表需要注意哪些事项：

https://www.cnblogs.com/zjfjava/p/6920407.html



##### sql查询数据需要注意哪些事项：

- SELECT关键字的顺序不能颠倒

SELECT ... FROM ... WHERE ... GROUP BY ... HAVING ... ORDER BY …LIMIT

- 生产环境下因为列数相对较多，一般禁用 SELECT *

- WHERE字段为避免全表扫描，一般需要增加索引



##### SQL 函数有哪些？

算术函数、字符串函数、日期函数、转换函数、聚合函数

聚合函数

• COUNT() 行数

• MAX() 最大值

• MIN() 最小值

• SUM() 求和

• AVG() 平均值

注意：聚合函数忽略空行



##### 什么是子查询？

需要从查询结果集中再次进行查询，才能得到想要的结果。

##### 子查询需要关注的问题？

• 关联子查询与非关联子查询区别。

• 何时使用 IN，何时使用 EXISTS。