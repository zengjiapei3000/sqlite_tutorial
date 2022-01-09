# IS NULL

**Summary**: in this tutorial, you will learn how to use the SQLite `IS NULL` and `IS NOT NULL` operators to check whether a value is NULL or not.

## Introduction to the SQLite IS NULL operator

`NULL` is special. It indicates that a piece of information is unknown or not applicable.

For example, some songs may not have the songwriter information because we don’t know who wrote them.

To store these unknown songwriters along with the songs in a database table, we must use NULL.

NULL is **not equal to** anything even the number zero, an empty string, and so on.

Especially, NULL is not equal to **itself**. The following expression returns 0:

```
NULL = NULL
```

This is because two unknown information cannot be comparable.

Let’s see the following `tracks` table from the sample database:

The following statement attempts to find tracks whose composers are NULL:

```
SELECT
    Name, 
    Composer
FROM
    tracks
WHERE
    Composer = NULL;
```

It returns an empty row without issuing any additional message.

This is because the following expression always evaluates to false:

```
Composer = NULL
```

It’s not valid to use the NULL this way.

To check if a value is NULL or not, you use the IS NULL operator instead:

```
{ column | expression } IS NULL;
```

The `IS NULL` operator returns 1 if the `column` or `expression` evaluates to NULL.

To find all tracks whose composers are unknown, you use the `IS NULL` operator as shown in the following query:

```
SELECT
    Name, 
    Composer
FROM
    tracks
WHERE
    Composer IS NULL
ORDER BY 
    Name;
```

## SQLite IS NOT NULL operator

The `NOT` operator negates the `IS NULL` operator as follows:

```
expression | column IS NOT NULL
```

The `IS NOT NULL` operator returns 1 if the `expression` or `column` is not NULL, and 0 if the `expression` or column is `NULL`.

The following example finds `tracks` whose composers are not NULL:

```
SELECT
    Name, 
    Composer
FROM
    tracks
WHERE
    Composer IS NOT NULL
ORDER BY 
    Name;
```