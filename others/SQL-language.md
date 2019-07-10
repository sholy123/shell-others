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
9. left join 
10. right join
11. union