# SELECT
SELECT 表示选择某一列数据。

## SELECT 简单语句

SELECT 可以跟单个表达式;

```
SELECT	1 + 1;
```

`2`

SELECT 可以跟多个表达式;

```
SELECT
    10 / 5,
    2 * 4;
```

`2|8`

---
## 用 SELECT 声明在表中查询数据

最复杂的 SELECT 声明:

```
SELECT DISTINCT column_list
FROM table_list
  JOIN table ON join_condition
WHERE row_filter
ORDER BY column
LIMIT count OFFSET offset
GROUP BY column
HAVING group_filter;
```
其中包含很多 SELECT 的子句:
>Use `ORDER BY` clause to sort the result set
>Use `DISTINCT` clause to query unique rows in a table.
>Use `WHERE` clause to filter rows in the result set.
>Use `LIMIT OFFSET` clauses to constrain the number of rows returned.
>Use `INNER JOIN` or `LEFT JOIN` to query data from multiple tables using join.
>Use `GROUP BY` to get the group rows into groups and apply aggregate function for each group.
>Use `HAVING` clause to filter groups.

### 从某一个表格中选取列(们)
```
SELECT 
    column_list(column1, column2, ...)
FROM 
    table;
```

- ***号** 表示 SELECT 全部的列

```
SELECT * FROM table
```
- *号 不应在实际中使用:

1. 当您开发应用程序时，您应该控制 SQLite 返回给您的应用程序的内容。假设一个表有 3 列，您使用星号 (*) 从所有三列中检索数据。

2. 如果有人删除了一列，您的应用程序将无法正常工作，因为它假设返回了三列，并且处理这三列的逻辑将被破坏。

3. 如果有人添加更多列，您的应用程序可能会工作，但它获得的数据比需要的多，这会在数据库和应用程序之间产生更多的 I/O 开销。
