# ORDER BY


ORDER BY 子句一般跟在 SELECT 之后，用于对选出的数据进行排序。

```
SELECT
   select_list
FROM
   table
ORDER BY
    column_1 ASC,
    column_2 DESC;
```

`ORDER BY`后跟排序依据的列，`ASC`表示升序排列，`DESC`表示降序排列。

ASC 可以省略:

```
SELECT
   select_list
FROM
   table
ORDER BY
    column_1,
    column_2 DESC;
```

## ORDER BY 使用列位置代替列名

```
SELECT
	name,
	milliseconds, 
	albumid
FROM
	tracks
ORDER BY
	 3,2;
```
列位置是在 SELECT 子句中的位置。

## ORDER BY 遇到 NULL 值的情况 

NULL 是特殊的。表示信息缺失或数据不适用，可以用在数据库中未知的某一个数据上。
NULL 是特殊的，因为您无法将它与另一个值进行比较。简单地说，如果这两条信息是未知的，你就无法比较它们。
NULL 甚至无法与自身进行比较；NULL 不等于自身，因此`NULL = NULL`总是导致错误。

在**排序**时，SQLite 认为 NULL 比任何其他值都小。
这意味着如果您使用 ASC，则 NULL 将出现在结果集的开头，或者当您使用 DESC 时，将出现在结果集的末尾。

SQLite 3.30.0在`ORDER BY`子句中添加了`NULLS FIRST`和`NULLS LAST`选项。该`NULLS FIRST`选项指定 NULL 将出现在结果集的开头，而该`NULLS LAST`选项将 NULL 放在结果集的末尾。
```
SELECT 
    TrackId, 
    Name, 
    Composer 
FROM 
    tracks
ORDER BY 
    Composer NULLS LAST(/NULL FIRST);
```