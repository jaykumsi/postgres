![Tinitiate POSTGRES Training](../images/sqlserver.png)
# POSTGRES SQL DQL - Data Query Language
> (c) Jay Kumsi / Tinitiate.com

* Data Query Language (DQL) is a set of SQL statements that are used to retrieve data from a database. DQL statements are used to select, filter, and sort data from tables, views, and other database objects.

 
## INNER JOIN
An INNER JOIN returns only the rows where there is a match in both tables.
```sql
SELECT employees.employee_id, employees.employee_name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.department_id;
``` 

## LEFT JOIN (or LEFT OUTER JOIN):

A LEFT JOIN returns all rows from the left table (employees) and the matched rows from the right table (departments). 
If there is no match, NULL values are returned for columns from the right table.

SELECT employees.employee_id, employees.employee_name, departments.department_name
FROM employees
LEFT JOIN departments ON employees.department_id = departments.department_id;


## RIGHT JOIN (or RIGHT OUTER JOIN):
A RIGHT JOIN returns all rows from the right table and the matched rows from the left table. 
If there is no match, NULL values are returned for columns from the left table.

SELECT employees.employee_id, employees.employee_name, departments.department_name
FROM employees
RIGHT JOIN departments ON employees.department_id = departments.department_id;

## FULL JOIN (or FULL OUTER JOIN):
A FULL JOIN returns all rows when there is a match in either the left or right table. 
If there is no match, NULL values are returned for columns from the table without a match.

SELECT employees.employee_id, employees.employee_name, departments.department_name
FROM employees
FULL JOIN departments ON employees.department_id = departments.department_id;


## CROSS JOIN:
A CROSS JOIN returns the Cartesian product of the two tables, meaning it returns all possible combinations of rows from the two tables.

SELECT employees.employee_id, employees.employee_name, departments.department_name
FROM employees
CROSS JOIN departments;


## SELF JOIN:
A SELF JOIN is a regular join, but the table is joined with itself.

SELECT e1.employee_name AS employee, e2.employee_name AS manager
FROM employees e1
INNER JOIN employees e2 ON e1.manager_id = e2.employee_id;



