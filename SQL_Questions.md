# SQL Practice Questions and Solutions

## Table of Contents

- [Select Operations](#select-operations)
- [Basic Joins](#basic-joins)
- [Basic Aggregate Functions](#basic-aggregate-functions)
- [Sorting and Grouping](#sorting-and-grouping)

## Select Operations

### 1. Low Fat and Recyclable Products

**Problem:** Find the ids of products that are both low fat and recyclable.

**Input:**

```sql
Products table:
+-------------+----------+------------+
| product_id  | low_fats | recyclable |
+-------------+----------+------------+
| 0           | Y        | N          |
| 1           | Y        | Y          |
| 2           | N        | Y          |
| 3           | Y        | Y          |
| 4           | N        | N          |
+-------------+----------+------------+
```

**Output:**

```sql
+-------------+
| product_id  |
+-------------+
| 1           |
| 3           |
+-------------+
```

**Solution:**

```sql
SELECT product_id
FROM Products
WHERE low_fats = 'Y' AND recyclable = 'Y';
```

### 2. Customer Referrals

**Problem:** Find the names of customers not referred by customer id = 2.

**Input:**

```sql
Customer table:
+----+------+------------+
| id | name | referee_id |
+----+------+------------+
| 1  | Will | null       |
| 2  | Jane | null       |
| 3  | Alex | 2          |
| 4  | Bill | null       |
| 5  | Zack | 1          |
| 6  | Mark | 2          |
+----+------+------------+
```

**Output:**

```sql
+------+
| name |
+------+
| Will |
| Jane |
| Bill |
| Zack |
+------+
```

**Solution:**

```sql
SELECT name
FROM Customer
WHERE referee_id != 2 OR referee_id IS NULL;
```

### 3. Big Countries

**Problem:** Find countries that are:

- Have an area of at least 3 million km², OR
- Have a population of at least 25 million

**Input:**

```sql
World table:
+-------------+-----------+---------+------------+--------------+
| name        | continent | area    | population | gdp          |
+-------------+-----------+---------+------------+--------------+
| Afghanistan | Asia      | 652230  | 25500100   | 20343000000 |
| Albania     | Europe    | 28748   | 2831741    | 12960000000 |
| Algeria     | Africa    | 2381741 | 37100000   | 188681000000|
| Andorra     | Europe    | 468     | 78115      | 3712000000  |
| Angola      | Africa    | 1246700 | 20609294   | 100990000000|
+-------------+-----------+---------+------------+--------------+
```

**Solution:**

```sql
SELECT name, population, area
FROM World
WHERE population >= 25000000 OR area >= 3000000;
```

[Continue with remaining questions in same format...]

## Basic Joins

[Continue formatting remaining join questions...]

## Basic Aggregate Functions

[Continue formatting remaining aggregate function questions...]

## Sorting and Grouping

[Continue formatting remaining sorting and grouping questions...]

## Tips for Revision

- Review questions by topic (Select, Joins, Aggregates, etc.)
- Practice writing solutions before checking answers
- Pay attention to NULL handling in queries
- Understand the difference between WHERE and HAVING clauses
- Remember to check for edge cases in your solutions

## Common SQL Functions Used

- LENGTH()
- COUNT()
- AVG()
- ROUND()
- DATE functions (INTERVAL, DATEDIFF)
- String functions
- Aggregate functions

## Common SQL Concepts Covered

- Basic SELECT operations
- Filtering with WHERE
- JOIN operations (LEFT, INNER)
- NULL handling
- Grouping and aggregation
- Date manipulation
- String operations

### 4. Authors Viewing Their Articles

**Problem:** Find all authors that viewed at least one of their own articles.

**Input:**

```sql
Views table:
+------------+-----------+-----------+------------+
| article_id | author_id | viewer_id | view_date  |
+------------+-----------+-----------+------------+
| 1          | 3         | 5         | 2019-08-01 |
| 1          | 3         | 6         | 2019-08-02 |
| 2          | 7         | 7         | 2019-08-01 |
| 2          | 7         | 6         | 2019-08-02 |
| 4          | 7         | 1         | 2019-07-22 |
| 3          | 4         | 4         | 2019-07-21 |
| 3          | 4         | 4         | 2019-07-21 |
+------------+-----------+-----------+------------+
```

**Output:**

```sql
+------+
| id   |
+------+
| 4    |
| 7    |
+------+
```

**Solution:**

```sql
SELECT DISTINCT author_id AS id
FROM Views
WHERE author_id = viewer_id
ORDER BY author_id ASC;
```

### 5. Invalid Tweets

**Problem:** Find tweets where the content length is strictly greater than 15 characters.

**Input:**

```sql
Tweets table:
+----------+----------------------------------+
| tweet_id | content                          |
+----------+----------------------------------+
| 1        | Let us Code                      |
| 2        | More than fifteen chars are here!|
+----------+----------------------------------+
```

**Output:**

```sql
+----------+
| tweet_id |
+----------+
| 2        |
+----------+
```

**Solution:**

```sql
SELECT tweet_id
FROM Tweets
WHERE LENGTH(content) > 15;
```

## Basic Joins

### 6. Employee Unique IDs

**Problem:** Show the unique ID of each user. If no unique ID exists, show null.

**Input:**

```sql
Employees table:
+----+----------+
| id | name     |
+----+----------+
| 1  | Alice    |
| 7  | Bob      |
| 11 | Meir     |
| 90 | Winston  |
| 3  | Jonathan |
+----+----------+

EmployeeUNI table:
+----+-----------+
| id | unique_id |
+----+-----------+
| 3  | 1         |
| 11 | 2         |
| 90 | 3         |
+----+-----------+
```

**Solution:**

```sql
SELECT unique_id, name
FROM Employees Emp
LEFT JOIN EmployeeUNI EmpU ON Emp.id = EmpU.id;
```

### 7. Product Sales Analysis

**Problem:** Report the product_name, year, and price for each sale_id.

**Input:**

```sql
Sales table:
+---------+------------+------+----------+-------+
| sale_id | product_id | year | quantity | price |
+---------+------------+------+----------+-------+
| 1       | 100        | 2008 | 10       | 5000  |
| 2       | 100        | 2009 | 12       | 5000  |
| 7       | 200        | 2011 | 15       | 9000  |
+---------+------------+------+----------+-------+

Product table:
+------------+--------------+
| product_id | product_name |
+------------+--------------+
| 100        | Nokia        |
| 200        | Apple        |
| 300        | Samsung      |
+------------+--------------+
```

**Solution:**

```sql
SELECT product_name, year, price
FROM Sales s
JOIN Product p ON s.product_id = p.product_id;
```

### 8. Customer Visits Analysis

**Problem:** Find users who visited without making transactions and count such visits.

**Input:**

```sql
Visits table:
+----------+-------------+
| visit_id | customer_id |
+----------+-------------+
| 1        | 23          |
| 2        | 9           |
| 4        | 30          |
| 5        | 54          |
| 6        | 96          |
| 7        | 54          |
| 8        | 54          |
+----------+-------------+

Transactions table:
+----------------+----------+--------+
| transaction_id | visit_id | amount |
+----------------+----------+--------+
| 2              | 5        | 310    |
| 3              | 5        | 300    |
| 9              | 5        | 200    |
| 12             | 1        | 910    |
| 13             | 2        | 970    |
+----------------+----------+--------+
```

**Solution:**

```sql
SELECT customer_id, COUNT(customer_id) as count_no_trans
FROM Visits v
LEFT JOIN Transactions t ON v.visit_id = t.visit_id
WHERE transaction_id IS NULL
GROUP BY customer_id;
```

### 9. Rising Temperature

**Problem:** Find dates' id with higher temperatures compared to the previous day.

**Input:**

```sql
Weather table:
+----+------------+-------------+
| id | recordDate | temperature |
+----+------------+-------------+
| 1  | 2015-01-01 | 10         |
| 2  | 2015-01-02 | 25         |
| 3  | 2015-01-03 | 20         |
| 4  | 2015-01-04 | 30         |
+----+------------+-------------+
```

**Solution:**

```sql
SELECT w1.id
FROM Weather w1
JOIN Weather w2
ON w1.recordDate = w2.recordDate + INTERVAL 1 DAY
WHERE w1.temperature > w2.temperature;
```

### 10. Machine Processing Time

**Problem:** Find the average time each machine takes to complete a process.

**Input:**

```sql
Activity table:
+------------+------------+---------------+-----------+
| machine_id | process_id | activity_type | timestamp |
+------------+------------+---------------+-----------+
| 0          | 0          | start         | 0.712     |
| 0          | 0          | end           | 1.520     |
| 0          | 1          | start         | 3.140     |
| 0          | 1          | end           | 4.120     |
| 1          | 0          | start         | 0.550     |
| 1          | 0          | end           | 1.550     |
| 1          | 1          | start         | 0.430     |
| 1          | 1          | end           | 1.420     |
| 2          | 0          | start         | 4.100     |
| 2          | 0          | end           | 4.512     |
| 2          | 1          | start         | 2.500     |
| 2          | 1          | end           | 5.000     |
+------------+------------+---------------+-----------+
```

**Solution:**

```sql
SELECT a1.machine_id,
       ROUND(AVG(a2.timestamp - a1.timestamp), 3) as processing_time
FROM Activity a1
JOIN Activity a2
ON a1.machine_id = a2.machine_id
AND a1.process_id = a2.process_id
AND a1.activity_type = 'start'
AND a2.activity_type = 'end'
GROUP BY a1.machine_id;
```

### 11. Employee Bonus

**Problem:** Report the name and bonus amount of each employee with a bonus less than 1000.

**Input:**

```sql
Employee table:
+-------+--------+------------+--------+
| empId | name   | supervisor | salary |
+-------+--------+------------+--------+
| 3     | Brad   | null       | 4000   |
| 1     | John   | 3          | 1000   |
| 2     | Dan    | 3          | 2000   |
| 4     | Thomas | 3          | 4000   |
+-------+--------+------------+--------+

Bonus table:
+-------+-------+
| empId | bonus |
+-------+-------+
| 2     | 500   |
| 4     | 2000  |
+-------+-------+
```

**Solution:**

```sql
SELECT name, bonus
FROM Employee e
LEFT JOIN Bonus b ON e.empId = b.empId
WHERE bonus < 1000 OR bonus IS NULL;
```

### 12. Students and Examinations

**Problem:** Find the number of times each student attended each exam.

**Input:**

```sql
Students table:
+------------+--------------+
| student_id | student_name |
+------------+--------------+
| 1          | Alice        |
| 2          | Bob          |
| 13         | John         |
| 6          | Alex         |
+------------+--------------+

Subjects table:
+--------------+
| subject_name |
+--------------+
| Math         |
| Physics      |
| Programming  |
+--------------+

Examinations table:
+------------+--------------+
| student_id | subject_name |
+------------+--------------+
| 1          | Math         |
| 1          | Physics      |
| 1          | Programming  |
| 2          | Programming  |
| 1          | Physics      |
| 1          | Math         |
| 13         | Math         |
| 13         | Programming  |
| 13         | Physics      |
| 2          | Math         |
| 1          | Math         |
+------------+--------------+
```

**Solution:**

```sql
SELECT s.student_id,
       s.student_name,
       sub.subject_name,
       COUNT(e.student_id) as attended_exams
FROM Students s
CROSS JOIN Subjects sub
LEFT JOIN Examinations e
ON s.student_id = e.student_id
AND sub.subject_name = e.subject_name
GROUP BY s.student_id, s.student_name, sub.subject_name
ORDER BY s.student_id, sub.subject_name;
```

### 13. Managers with Five Direct Reports

**Problem:** Find managers with at least five direct reports.

**Input:**

```sql
Employee table:
+-----+-------+------------+-----------+
| id  | name  | department | managerId |
+-----+-------+------------+-----------+
| 101 | John  | A          | null      |
| 102 | Dan   | A          | 101       |
| 103 | James | A          | 101       |
| 104 | Amy   | A          | 101       |
| 105 | Anne  | A          | 101       |
| 106 | Ron   | B          | 101       |
+-----+-------+------------+-----------+
```

**Solution:**

```sql
SELECT name
FROM Employee
WHERE id IN (
    SELECT managerId
    FROM Employee
    GROUP BY managerId
    HAVING COUNT(*) >= 5
);
```

### 14. User Confirmation Rate

**Problem:** Find the confirmation rate of each user.

**Input:**

```sql
Signups table:
+---------+---------------------+
| user_id | time_stamp         |
+---------+---------------------+
| 3       | 2020-03-21 10:16:13|
| 7       | 2020-01-04 13:57:59|
| 2       | 2020-07-29 23:09:44|
| 6       | 2020-12-09 10:39:37|
+---------+---------------------+

Confirmations table:
+---------+---------------------+-----------+
| user_id | time_stamp         | action    |
+---------+---------------------+-----------+
| 3       | 2021-01-06 03:30:46| timeout   |
| 3       | 2021-07-14 14:00:00| timeout   |
| 7       | 2021-06-12 11:57:29| confirmed |
| 7       | 2021-06-13 12:58:28| confirmed |
| 7       | 2021-06-14 13:59:27| confirmed |
| 2       | 2021-01-22 00:00:00| confirmed |
| 2       | 2021-02-28 23:59:59| timeout   |
+---------+---------------------+-----------+
```

**Solution:**

```sql
SELECT
    s.user_id,
    ROUND(IFNULL(
        SUM(CASE WHEN c.action = 'confirmed' THEN 1 ELSE 0 END) /
        COUNT(c.action),
        0
    ), 2) as confirmation_rate
FROM Signups s
LEFT JOIN Confirmations c ON s.user_id = c.user_id
GROUP BY s.user_id;
```

### 15. Not Boring Movies

**Problem:** Report movies with odd-numbered ID and non-boring descriptions.

**Input:**

```sql
Cinema table:
+----+------------+-------------+--------+
| id | movie      | description | rating |
+----+------------+-------------+--------+
| 1  | War        | great 3D    | 8.9    |
| 2  | Science    | fiction     | 8.5    |
| 3  | irish      | boring      | 6.2    |
| 4  | Ice song   | Fantacy     | 8.6    |
| 5  | House card | Interesting | 9.1    |
+----+------------+-------------+--------+
```

**Solution:**

```sql
SELECT *
FROM Cinema
WHERE description != 'boring' AND id % 2 != 0
ORDER BY rating DESC;
```

### 16. Average Selling Price

**Problem:** Find the average selling price for each product.

**Input:**

```sql
Prices table:
+------------+------------+------------+--------+
| product_id | start_date | end_date   | price  |
+------------+------------+------------+--------+
| 1          | 2019-02-17 | 2019-02-28 | 5      |
| 1          | 2019-03-01 | 2019-03-22 | 20     |
| 2          | 2019-02-01 | 2019-02-20 | 15     |
| 2          | 2019-02-21 | 2019-03-31 | 30     |
+------------+------------+------------+--------+

UnitsSold table:
+------------+---------------+-------+
| product_id | purchase_date | units |
+------------+---------------+-------+
| 1          | 2019-02-25    | 100   |
| 1          | 2019-03-01    | 15    |
| 2          | 2019-02-10    | 200   |
| 2          | 2019-03-22    | 30    |
+------------+---------------+-------+
```

**Solution:**

```sql
SELECT
    p.product_id,
    ROUND(SUM(p.price * u.units) / SUM(u.units), 2) as average_price
FROM Prices p
JOIN UnitsSold u
ON p.product_id = u.product_id
AND u.purchase_date BETWEEN p.start_date AND p.end_date
GROUP BY p.product_id;
```

### 17. Project Employee Average

**Problem:** Find the average experience years for each project.

**Input:**

```sql
Project table:
+-------------+-------------+
| project_id  | employee_id |
+-------------+-------------+
| 1           | 1           |
| 1           | 2           |
| 1           | 3           |
| 2           | 1           |
| 2           | 4           |
+-------------+-------------+

Employee table:
+-------------+--------+------------------+
| employee_id | name   | experience_years |
+-------------+--------+------------------+
| 1           | Khaled | 3                |
| 2           | Ali    | 2                |
| 3           | John   | 1                |
| 4           | Doe    | 2                |
+-------------+--------+------------------+
```

**Solution:**

```sql
SELECT
    p.project_id,
    ROUND(AVG(e.experience_years), 2) AS average_years
FROM Project p
JOIN Employee e ON p.employee_id = e.employee_id
GROUP BY p.project_id;
```

### 18. User Contest Percentage

**Problem:** Find the percentage of users registered in each contest.

**Input:**

```sql
Users table:
+---------+-----------+
| user_id | user_name |
+---------+-----------+
| 6       | Alice     |
| 2       | Bob       |
| 7       | Alex      |
+---------+-----------+

Register table:
+------------+---------+
| contest_id | user_id |
+------------+---------+
| 215        | 6       |
| 209        | 2       |
| 208        | 2       |
| 210        | 6       |
| 208        | 6       |
| 209        | 7       |
| 209        | 6       |
| 215        | 7       |
| 208        | 7       |
| 210        | 2       |
| 207        | 2       |
| 210        | 7       |
+------------+---------+
```

**Solution:**

```sql
SELECT
    contest_id,
    ROUND(COUNT(DISTINCT user_id) * 100.0 /
        (SELECT COUNT(DISTINCT user_id) FROM Users), 2) AS percentage
FROM Register
GROUP BY contest_id
ORDER BY percentage DESC, contest_id;
```

### 19. Query Quality Analysis

**Problem:** Find query quality and poor query percentage for each query_name.

**Input:**

```sql
Queries table:
+------------+-------------------+----------+--------+
| query_name | result           | position | rating |
+------------+-------------------+----------+--------+
| Dog        | Golden Retriever | 1        | 5      |
| Dog        | German Shepherd  | 2        | 5      |
| Dog        | Mule            | 200      | 1      |
| Cat        | Shirazi         | 5        | 2      |
| Cat        | Siamese         | 3        | 3      |
| Cat        | Sphynx          | 7        | 4      |
+------------+-------------------+----------+--------+
```

**Solution:**

```sql
SELECT
    query_name,
    ROUND(AVG(rating/position), 2) as quality,
    ROUND(SUM(CASE WHEN rating < 3 THEN 1 ELSE 0 END) * 100.0 / COUNT(*), 2)
        as poor_query_percentage
FROM Queries
GROUP BY query_name;
```

### 20. Monthly Transactions

**Problem:** Find monthly statistics for transactions by country.

**Input:**

```sql
Transactions table:
+------+---------+----------+--------+------------+
| id   | country | state    | amount | trans_date |
+------+---------+----------+--------+------------+
| 121  | US      | approved | 1000   | 2018-12-18 |
| 122  | US      | declined | 2000   | 2018-12-19 |
| 123  | US      | approved | 2000   | 2019-01-01 |
| 124  | DE      | approved | 2000   | 2019-01-07 |
+------+---------+----------+--------+------------+
```

**Solution:**

```sql
SELECT
    DATE_FORMAT(trans_date, '%Y-%m') as month,
    country,
    COUNT(*) as trans_count,
    SUM(CASE WHEN state = 'approved' THEN 1 ELSE 0 END) as approved_count,
    SUM(amount) as trans_total_amount,
    SUM(CASE WHEN state = 'approved' THEN amount ELSE 0 END) as approved_total_amount
FROM Transactions
GROUP BY DATE_FORMAT(trans_date, '%Y-%m'), country;
```

### 21. Immediate Food Delivery

**Problem:** Find the percentage of immediate orders in the first orders of all customers.

**Input:**

```sql
Delivery table:
+-------------+-------------+------------+-----------------------------+
| delivery_id | customer_id | order_date | customer_pref_delivery_date|
+-------------+-------------+------------+-----------------------------+
| 1           | 1           | 2019-08-01 | 2019-08-02                |
| 2           | 2           | 2019-08-02 | 2019-08-02                |
| 3           | 1           | 2019-08-11 | 2019-08-12                |
| 4           | 3           | 2019-08-24 | 2019-08-24                |
| 5           | 3           | 2019-08-21 | 2019-08-22                |
| 6           | 2           | 2019-08-11 | 2019-08-13                |
| 7           | 4           | 2019-08-09 | 2019-08-09                |
+-------------+-------------+------------+-----------------------------+
```

**Solution:**

```sql
WITH FirstOrders AS (
    SELECT
        customer_id,
        MIN(order_date) as first_order_date
    FROM Delivery
    GROUP BY customer_id
)
SELECT
    ROUND(
        SUM(CASE
            WHEN order_date = customer_pref_delivery_date THEN 1
            ELSE 0
        END) * 100.0 / COUNT(*),
        2
    ) as immediate_percentage
FROM Delivery d
JOIN FirstOrders fo
    ON d.customer_id = fo.customer_id
    AND d.order_date = fo.first_order_date;
```

### 22. Player Login Analysis

**Problem:** Find the fraction of players that logged in again on the day after their first login.

**Input:**

```sql
Activity table:
+-----------+-----------+------------+--------------+
| player_id | device_id | event_date | games_played |
+-----------+-----------+------------+--------------+
| 1         | 2         | 2016-03-01 | 5            |
| 1         | 2         | 2016-03-02 | 6            |
| 2         | 3         | 2017-06-25 | 1            |
| 3         | 1         | 2016-03-02 | 0            |
| 3         | 4         | 2018-07-03 | 5            |
+-----------+-----------+------------+--------------+
```

**Solution:**

```sql
WITH FirstLogins AS (
    SELECT player_id, MIN(event_date) as first_login
    FROM Activity
    GROUP BY player_id
),
ConsecutiveLogins AS (
    SELECT
        f.player_id,
        CASE WHEN EXISTS (
            SELECT 1
            FROM Activity a2
            WHERE a2.player_id = f.player_id
            AND a2.event_date = DATE_ADD(f.first_login, INTERVAL 1 DAY)
        ) THEN 1 ELSE 0 END as logged_in_next_day
    FROM FirstLogins f
)
SELECT ROUND(
    SUM(logged_in_next_day) / COUNT(*),
    2
) as fraction
FROM ConsecutiveLogins;
```

## SQL Concepts Summary

### Key Concepts Covered:

1. Basic SELECT operations
2. JOIN operations (INNER, LEFT, CROSS)
3. Aggregation functions (COUNT, SUM, AVG)
4. Date manipulation
5. Window functions
6. Common Table Expressions (CTEs)
7. Conditional logic (CASE statements)
8. NULL handling
9. String operations
10. Percentage calculations

### Common SQL Functions Used:

- Aggregate: COUNT(), SUM(), AVG()
- Date: DATE_FORMAT(), DATE_ADD(), INTERVAL
- Numeric: ROUND()
- String: LENGTH()
- Conditional: CASE, IF, IFNULL
- Window Functions: LAG()

### Best Practices:

1. Always handle NULL values appropriately
2. Use meaningful aliases for better readability
3. Format queries with proper indentation
4. Use CTEs for complex queries
5. Consider performance implications with large datasets
6. Use appropriate JOIN types based on requirements
7. Remember to handle edge cases
8. Use proper indexing for better performance

### Tips for Practice:

1. Start with simple queries and gradually increase complexity
2. Understand the problem requirements thoroughly
3. Test your solutions with edge cases
4. Practice writing queries without looking at solutions
5. Focus on query optimization
6. Learn to read and understand execution plans
7. Regular practice with varied problem types
