# WHERE

## Introduction to SQLite WHERE clause
The `WHERE` clause is an optional clause of the SELECT statement. It appears after the `FROM` clause as the following statement:
```
SELECT
	column_list
FROM
	table
WHERE
	search_condition;
```

The search condition in the `WHERE` has the following form:
```
left_expression COMPARISON_OPERATOR right_expression
```

For example, you can form a search condition as follows:
```
WHERE column_1 = 100;

WHERE column_2 IN (1,2,3);

WHERE column_3 LIKE 'An%';

WHERE column_4 BETWEEN 10 AND 20;
```

>**TIP**: Besides the `SELECT` statement, you can use the `WHERE` clause in the `UPDATE` and `DELETE` statements.

---
## SQLite comparison operators

A comparison operator tests if two expressions are the same.

| **Operator** | **Meaning** |
| :- | :- |
| = | Equal to |
| <> or != | Not equal to |
| < | Less than |
| > | Greater than |
| <= | 	Less than or equal to |
| >= | Greater than or equal to |

## SQLite logical operators

Logical operators allow you to test the truth of some expressions. A logical operator returns `1`, `0`, or a `NULL` value.
Notice that SQLite does not provide Boolean data type therefore 1 means TRUE, and 0 means FALSE.

| **Operator** | **Meaning** |
| :- | :- |
| ALL | returns 1 if all expressions are 1. |
| AND | returns 1 if both expressions are 1, and 0 if one of the expressions is 0. |
| ANY | returns 1 if any one of a set of comparisons is 1. |
| BETWEEN | returns 1 if a value is within a range. |
| EXISTS | returns 1 if a subquery contains any rows. |
| IN | returns 1 if a value is in a list of values. |
| LIKE | returns 1 if a value matches a pattern. |
| NOT | reverses the value of other operators such as NOT EXISTS, NOT IN, NOT BETWEEN, etc. |
| OR | returns true if either expression is 1. |

---

## SQLite WHERE clause examples

### SQLite WHERE and equality operator example

the following query uses the `WHERE` clause and the equality operator(`=`) to find all the tracks in the album id 1:

```
SELECT
   name,
   milliseconds,
   bytes,
   albumid
FROM
   tracks
WHERE
   albumid = 1;
```

>**TIP**:
>
>1. SQLite 将AlbumId列中存储的值与文字值1进行比较以测试它们是否相等。只返回满足条件的行。
>2. 如果您比较不同数据类型中的值，例如字符串和数字，SQLite 必须执行隐式数据类型转换，但一般情况下，您应该避免这样做。

## SQLite WHERE clause with LIKE operator example

Sometimes, you may ***not remember*** exactly the data that you want to search. In this case, you perform an inexact search using the `LIKE` operator.

For example, to find which tracks composed by Smith, you use the `LIKE` operator as follows:

```
SELECT
	name,
	albumid,
	composer
FROM
	tracks
WHERE
	composer LIKE '%Smith%'
ORDER BY
	albumid;
```

## SQLite WHERE clause with the IN operator example

The `IN` operator allows you to check whether a value is in a list of a comma-separated list of values. 
For example, to find tracks that have media type id is 2 or 3, you use the `IN` operator as shown in the following statement:

```
SELECT
	name,
	albumid,
	mediatypeid
FROM
	tracks
WHERE
	mediatypeid IN (2, 3);
```