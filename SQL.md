# SQL Complete Guide: Basics to Advanced

## Table of Contents

1. [SQL Basics](#sql-basics)
2. [Intermediate SQL](#intermediate-sql)
3. [Advanced SQL](#advanced-sql)
4. [Interview Questions](#interview-questions)
5. [Performance Optimization](#performance-optimization)

## SQL Basics

### 1. Introduction to Databases

- Database: Organized collection of structured data
- RDBMS: Relational Database Management System
- Popular RDBMS: MySQL, PostgreSQL, Oracle, SQL Server

### 2. Basic SQL Commands

```sql
-- SELECT: Retrieve data
SELECT column1, column2 FROM table_name;

-- INSERT: Add new records
INSERT INTO table_name (column1, column2) VALUES (value1, value2);

-- UPDATE: Modify existing records
UPDATE table_name SET column1 = value1 WHERE condition;

-- DELETE: Remove records
DELETE FROM table_name WHERE condition;
```

### 3. Basic Clauses

- WHERE: Filter records
- ORDER BY: Sort results
- GROUP BY: Group rows that have the same values
- HAVING: Filter groups
- LIMIT/OFFSET: Restrict number of rows returned

### Basic Interview Questions

1. What is the difference between DELETE and TRUNCATE?

   - DELETE removes specific rows and can be rolled back
   - TRUNCATE removes all rows, can't be rolled back, resets auto-increment

2. What is the difference between CHAR and VARCHAR?

   - CHAR is fixed length
   - VARCHAR is variable length

3. Explain primary key and foreign key
   - Primary key: Unique identifier for each record
   - Foreign key: References primary key of another table

## Intermediate SQL

### 1. Joins

```sql
-- INNER JOIN
SELECT * FROM table1
INNER JOIN table2 ON table1.id = table2.id;

-- LEFT JOIN
SELECT * FROM table1
LEFT JOIN table2 ON table1.id = table2.id;

-- RIGHT JOIN
SELECT * FROM table2
RIGHT JOIN table1 ON table1.id = table2.id;

-- FULL OUTER JOIN
SELECT * FROM table1
FULL OUTER JOIN table2 ON table1.id = table2.id;
```

### 2. Subqueries

```sql
-- Single row subquery
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);

-- Multiple row subquery
SELECT * FROM employees
WHERE department_id IN (SELECT id FROM departments WHERE location = 'NY');
```

### 3. Functions

- String functions: CONCAT, SUBSTRING, UPPER, LOWER
  1. REGEXP/RLIKE: Pattern matching using regular expressions
  ```sql
  -- Basic REGEXP usage
  SELECT column_name FROM table_name WHERE column_name REGEXP 'pattern';
  
  -- Common REGEXP patterns:
  -- Find emails
  SELECT email FROM users WHERE email REGEXP '^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$';
  
  -- Find phone numbers (XXX-XXX-XXXX format)
  SELECT phone FROM contacts WHERE phone REGEXP '^[0-9]{3}-[0-9]{3}-[0-9]{4}$';
  
  -- Words starting with 'A'
  SELECT name FROM customers WHERE name REGEXP '^A';
  
  -- Words containing numbers
  SELECT product_name FROM products WHERE product_name REGEXP '[0-9]';
  
  -- Multiple patterns using |
  SELECT city FROM addresses WHERE city REGEXP 'New York|London|Paris';
  
  -- Numeric functions: ROUND, CEIL, FLOOR
    1. COALESCE: Returns first non-null value in a list
    ```sql
    -- Basic COALESCE usage
    SELECT COALESCE(column1, column2, 'default_value') FROM table_name;
    
    -- Practical example with employee bonus
    SELECT employee_name,
           COALESCE(bonus, commission, base_salary * 0.1) as final_bonus
    FROM employees;
  ```
  - Date functions: 
    1. DATEADD/DATE_ADD: Add interval to date
    ```sql
    -- Add 5 days to current date
    SELECT DATE_ADD(CURRENT_DATE, INTERVAL 5 DAY);
    -- Add 2 months to a date
    SELECT DATE_ADD('2023-01-01', INTERVAL 2 MONTH);
  ```
  - Aggregate functions: COUNT, SUM, AVG, MAX, MIN

### Intermediate Interview Questions

1. What is the difference between UNION and UNION ALL?

   - UNION removes duplicates
   - UNION ALL keeps duplicates

2. Explain different types of joins with examples

   - INNER JOIN: Returns matching records from both tables
   - LEFT JOIN: Returns all records from left table and matching from right
   - RIGHT JOIN: Returns all records from right table and matching from left
   - FULL JOIN: Returns all records when there's a match in either table

3. What are aggregate functions? Why can't we use WHERE with them?
   - Aggregate functions work on a group of rows
   - WHERE filters individual rows before grouping
   - HAVING filters groups after grouping

## Advanced SQL

### 1. Window Functions

```sql
-- ROW_NUMBER
SELECT *,
       ROW_NUMBER() OVER (PARTITION BY department ORDER BY salary DESC) as rank
FROM employees;

-- Running totals
SELECT *,
       SUM(amount) OVER (ORDER BY date) as running_total
FROM sales;
```

### 2. Common Table Expressions (CTE)

```sql
WITH employee_hierarchy AS (
    SELECT employee_id, manager_id, level
    FROM employees
    WHERE manager_id IS NULL
    UNION ALL
    SELECT e.employee_id, e.manager_id, h.level + 1
    FROM employees e
    JOIN employee_hierarchy h ON e.manager_id = h.employee_id
)
SELECT * FROM employee_hierarchy;
```

### 3. PIVOT and UNPIVOT

```sql
-- PIVOT example
SELECT *
FROM (SELECT category, month, amount FROM sales) p
PIVOT (
    SUM(amount)
    FOR month IN (Jan, Feb, Mar, Apr)
);
```

### Advanced Interview Questions

1. Explain window functions and their use cases

   - Window functions perform calculations across rows
   - Common functions: ROW_NUMBER, RANK, DENSE_RANK, LAG, LEAD
   - Used for running totals, rankings, comparisons with previous rows

2. What is a recursive CTE and when would you use it?

   - Recursive CTEs are used for hierarchical or graph-like data
   - Common uses: organizational charts, bill of materials
   - Contains anchor member and recursive member

3. Explain transaction isolation levels
   - READ UNCOMMITTED: Dirty reads possible
   - READ COMMITTED: No dirty reads
   - REPEATABLE READ: Same reads in transaction
   - SERIALIZABLE: Highest isolation

## Performance Optimization

### 1. Indexing

- Types of indexes: B-tree, Hash, Bitmap
- When to use indexes
- Index maintenance and overhead

### 2. Query Optimization

```sql
-- Bad practice
SELECT * FROM large_table;

-- Good practice
SELECT specific_columns FROM large_table WHERE indexed_column = value;
```

### 3. EXPLAIN PLAN

- Understanding execution plans
- Identifying performance bottlenecks
- Query tuning strategies

### Performance Interview Questions

1. How would you optimize a slow query?

   - Check execution plan
   - Add appropriate indexes
   - Rewrite query to use indexes effectively
   - Consider partitioning for large tables

2. What are different types of indexes?

   - B-tree: Default, good for ranges
   - Hash: Exact matches only
   - Bitmap: Low cardinality columns

3. What is database normalization?
   - 1NF: Atomic values
   - 2NF: Single-column primary key
   - 3NF: No transitive dependencies

## Practice Problems

### Basic Level

1. Find employees earning more than average salary

```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

### Intermediate Level

1. Find departments with more than 3 employees

```sql
SELECT department_id, COUNT(*) as emp_count
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 3;
```

### Advanced Level

1. Find employees who earn more than their managers

```sql
SELECT e.name as employee, m.name as manager, e.salary as emp_salary, m.salary as mgr_salary
FROM employees e
JOIN employees m ON e.manager_id = m.employee_id
WHERE e.salary > m.salary;
```

## Tips for Interviews

1. Always clarify requirements before writing queries
2. Think about edge cases
3. Consider performance implications
4. Be prepared to explain your approach
5. Practice writing queries without IDE help

Remember to:

- Start with simple solutions
- Optimize only when necessary
- Test with sample data
- Consider NULL values
- Think about scalability
