## SQL语句的学习

这个部分主要是学习SQL的语句，其实很多的语句目前还不是很清楚，需要再认真学习一下，自己只会简单的用法，对于左连接、右连接这种稍微高级一点的其实还是不会的，所以还是需要自己学习一下，下面就是介绍简单的SQL语句。

### 基础教程

1. select选择语句
   
   - 示例：`select column１，column2 from tabel  OR select * from table`
   - 说明：筛选具体的表中的某一列或者是某几列，或者是*代表是所有的列。 
2. distinct
    - 示例：`select distinct column1 from table`
    - 说明：筛选该列中没有重复出现的字段
3. where
    - 示例：`select column from table where column=值`
    - 说明：这里的运算符有“＝，！＝，<>, > , <, >=, <=,like ,between”等几种方式
4. and && or 
    - 示例:`select column1,column2 from table where column1=1 and column2=2`
    - 示例：`select column1,column2 from table where column1=1 or column2=2`
    - 说明：选择column1和column2的值为1和2的值，and的意思是且，交集；or的意思是或者，并集
5. order by
    - 示例：```select * from table order by column1    #升序```
    - 示例：`select * from table order by column1 DESC  #降序`
    - 示例：`select * from table order by column1,column2`
    - 说明：按照column1升序的同时，若有多个重复值，column2按照升序排列
6. insert 
7. update
8. detele

### 高级一些的教程

1. Top (mysql里面好像没有)
2. like 
3. 通配符
4. in
5. between
6. aliases
7. join
8. inner join
   - 示例：`select p.name,p.age,q.name,q.age from p  inner join q on p.age=q.age order by p.age`
   - 说明：inner join 和join基本上是一致的，在表中至少一个匹配时，就返回相应的行
9.  left join 
    - 示例：`select column1 from table1 left join tabel2 on table1.column1=table2.column2`
    - 说明：leftjoin关键字会从左表那里返回所有的行，即使右表中没有匹配的行，左表指的是第一个表
10. right join
    - 示例：`select column1 from table1 right join tabel2 on table1.column1=table2.column2`
    - 说明：右连接会从右表中返回所有的行，即使左表中没有相应匹配的值。右表指的是第二个表
11. full join
    - 示例：`select column1 from table1 full join tabel2 on table1.column1=table2.column2` 
    - 说明：返回两个表中所有的行，没有匹配的值也会返回。
12.  union
    - 示例：`SELECT column_name(s) FROM table_name1 UNION SELECT column_name(s) FROM table_name2`
    - 说明：默认选择不同的值，如果允许重复的值，可以使用union all
13. select into
    - 示例：`select * into new-table[in external database] from old-table`
    - 说明：将old表中的数据查询出来插入一个新的表，用来做备份
14. create database
    - 示例：`create database database-name`
    - 说明：创建数据库
15. create table
    - 示例：`create table table-name( 列名称 数据类型，列名称2 数据类型，。。。)`
    - 说明：创建表
16. unique约束
    - unique约束唯一标识数据库中表的每条记录
    - 和主键一样均为列或列集合提供了唯一性的保证
    - 主键拥有自定义的unique约束
    - 每个表可以有多个unique约束，但主键约束只有一个
17. 主键
    - 每个表必须包含唯一主键，并且只能有一个主键
    - 主键的值不能为空
18. 外键
    - 一个表中的外键指向另一个表中的主键
19. 索引
    - 可以在表中创建索引，方便更加快速的查询，用户无法看见索引，它们只能用来加速搜索和查询
    - 示例：`create index index-name on table-name (column-name)`