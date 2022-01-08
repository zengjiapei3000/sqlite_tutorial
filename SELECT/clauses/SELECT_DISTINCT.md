# DISTINCT

`DISTINCT`子句是`SELECT`语句的可选子句  。该 DISTINCT 子句允许您删除结果集中的重复行。

## 一般用法

```
SELECT DISTINCT	select_list
FROM table;
```
在这个**语法**中：
- DISTINCT 必须在 SELECT 后；
- DISTINCT 后跟列，或 a list of column。如果使用**多个列**, 将使用多个列的值的结合（即多个列都重复的情况下会只留一条）来评估重复的数据。

### DISTINCT 处理 NULL

SQLite 认为NULL值是**重复**的。如果您将DISTINCT子句与具有NULL值的列一起使用，SQLite 将保留其中的一个NULL值。