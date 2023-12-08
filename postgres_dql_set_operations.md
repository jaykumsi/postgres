![Tinitiate POSTGRES Training](../images/sqlserver.png)
# POSTGRES SQL DQL - Data Query Language
> (c) Venkata Bhattaram / Tinitiate.com

## Data Query Language (DQL) Set Operations
* UNION
* Using Set Operations with Order By
* INTERSECT
* EXCEPT
 
 ## UNION
 The UNION operator is used to combine the results of two or more SELECT statements into a single result set, removing duplicate rows.

-- Example: Retrieve distinct department names from employees and departments tables
  SELECT department_name FROM employees
  UNION
  SELECT department_name FROM departments;


## INTERSECT
The INTERSECT operator returns the common rows that appear in the result sets of two SELECT statements.

-- Example: Retrieve common department names from employees and departments tables

SELECT department_name FROM employees
INTERSECT
SELECT department_name FROM departments;

## EXCEPT (or MINUS):
The EXCEPT (or MINUS in some databases) operator returns the distinct rows from the result set of the first SELECT statement that do not appear in the result set of the second SELECT statement.

-- Example: Retrieve department names from employees that do not exist in departments
SELECT department_name FROM employees
EXCEPT
SELECT department_name FROM departments;


## Using Set Operations with Order By:
When using set operations, you can include an ORDER BY clause in the first query only. The result set is ordered based on the ORDER BY clause of the first query.

-- Example: Retrieve distinct department names from employees and departments tables, ordered alphabetically
SELECT department_name FROM employees
UNION
SELECT department_name FROM departments
ORDER BY department_name;


