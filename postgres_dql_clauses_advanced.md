![Tinitiate POSTGRES Training](../images/sqlserver.png)
# POSTGRES SQL DQL - Data Query Language
> (c) Jay Kumsi / Tinitiate.com
* WINDOW Clause
* PARTITION BY Clause
* FETCH and OFFSET Clauses
* FOR UPDATE and FOR SHARE Clauses
* WITH Clause (Common Table Expressions - CTEs)
* LATERAL Join

## WINDOW Clause
 The WINDOW clause is used in conjunction with window functions to define named windows that can be referenced by multiple window functions within a SELECT statement.

```sql
SELECT
    column1,
    column2,
    SUM(column2) OVER my_window AS running_total
FROM
    your_table
WINDOW my_window AS (ORDER BY column1);


```

## PARTITION BY  Clause
 The PARTITION BY clause divides the result set into partitions to which the window function is applied separately. It's often used with aggregate and window functions.
 
```sql
SELECT
    column1,
    column2,
    AVG(column2) OVER (PARTITION BY column1) AS avg_per_partition
FROM
    your_table;

```
## FETCH and OFFSET Clauses
The FETCH and OFFSET clauses are used for result set pagination. They allow you to limit the number of rows returned and skip a specified number of rows.
* Data Prep
```sql
SELECT
    column1,
    column2
FROM
    your_table
ORDER BY column1
OFFSET 10
FETCH FIRST 5 ROWS ONLY;
```

## FOR UPDATE and FOR SHARE Clauses :
These clauses are used for controlling the behavior of the SELECT statement when dealing with concurrent transactions. 
FOR UPDATE locks the selected rows, preventing other transactions from modifying them until the current transaction is committed.
```sql
SELECT
    column1,
    column2
FROM
    your_table
WHERE
    column1 = 1
FOR UPDATE;
```

## WITH Clause (Common Table Expressions - CTEs):
The WITH clause allows you to define temporary result sets (CTEs) that you can reference within the context of a larger query.

```sql
WITH cte_name AS (
    SELECT
        column1,
        column2
    FROM
        your_table
)
SELECT
    *
FROM
    cte_name;
```

## LATERAL Join:
The LATERAL join allows a subquery to reference columns of the preceding tables in the FROM clause. It's useful for correlated subqueries.

```sql
SELECT
    column1,
    column2,
    (SELECT MAX(column2) FROM another_table WHERE another_table.id = your_table.id) AS max_value
FROM
    your_table;


```
