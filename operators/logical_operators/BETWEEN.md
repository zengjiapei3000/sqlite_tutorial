# BETWEEN

**Summary**: in this tutorial, you will learn how to use the SQLite `BETWEEN` operator to test whether a value is in a range of values.

---

## Introduction to SQLite BETWEEN Operator

1. The `BETWEEN` operator is a logical operator that tests whether a value is in range of values. 
2. If the value is in the specified range, the `BETWEEN` operator returns true. 
3. The `BETWEEN` operator can be used in the `WHERE` clause of the `SELECT`, `DELETE`, `UPDATE`, and `REPLACE` statements.

The following illustrates the syntax of the SQLite `BETWEEN` operator:

```
test_expression BETWEEN low_expression AND high_expression
```

In this syntax:
- `test_expression` is an expression to test for in the range defined by `low_expression` and `high_expression`.
- `low_expression` and `high_expression` is any valid expression that specify the low and high values of the range. The `low_expression` should be less than or equal to `high_expression`, or the BETWEEN is always returns false.
- The `AND` keyword is a placeholder which indicates the `test_expression` should be within the range specified by `low_expression` and `high_expression`.

**Note that** the `BETWEEN` operator is **inclusive**. It returns true when the `test_expression` is less than or equal to `high_expression` and greater than or equal to the value of `low_expression`:

```
test_expression >= low_expression AND test_expression <= high_expression
```

To specify an exclusive range, you use the greater than (>) and less than operators (<).

**Note that** if any input to the `BETWEEN` operator is NULL, the result is NULL, or unknown to be precise.

To negate the result of the `BETWEEN` operator, you use the `NOT BETWEEN` operator as follows:

```
test_expression NOT BETWEEN low_expression AND high_expression
```

The `NOT BETWEEN` returns true if the value of `test_expression` is less than the value of `low_expression` or greater than the value of `high_expression`:


## SQLite BETWEEN operator examples

### SQLite BETWEEN numeric values example

The following statement finds `invoices` whose total is between 14.96 and 18.86:

```
SELECT
    InvoiceId,
    BillingAddress,
    Total
FROM
    invoices
WHERE
    Total BETWEEN 14.91 and 18.86    
ORDER BY
    Total; 
```

### SQLite NOT BETWEEN numeric values example

To find the invoices whose total are not between 1 and 20, you use the `NOT BETWEEN` operator as shown in the following query:

```
SELECT
    InvoiceId,
    BillingAddress,
    Total
FROM
    invoices
WHERE
    Total NOT BETWEEN 1 and 20
ORDER BY
    Total;
```

### SQLite BETWEEN dates example

The following example finds invoices whose invoice dates are from `January 1 2010` and `January 31 2010`:

```
SELECT
    InvoiceId,
    BillingAddress,
    InvoiceDate,
    Total
FROM
    invoices
WHERE
    InvoiceDate BETWEEN '2010-01-01' AND '2010-01-31'
ORDER BY
    InvoiceDate;
```
### SQLite NOT BETWEEN dates example

The following statement finds invoices whose dates are not between `January 03, 2009`, and `December 01, 2013`:

```
SELECT
    InvoiceId,
    BillingAddress,
    date(InvoiceDate) InvoiceDate,
    Total
FROM
    invoices
WHERE
    InvoiceDate NOT BETWEEN '2009-01-03' AND '2013-12-01'
ORDER BY
    InvoiceDate;
```