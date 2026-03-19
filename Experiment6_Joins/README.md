# Experiment 6: Joins
## NAME: VIJAYAKUMAR S
## REG NO: 212224040359
## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

```sql
SELECT c.cust_name,c.city,c.grade,s.name as Salesman, s.city
FROM customer c 
Join salesman s
on c.salesman_id = s.salesman_id
WHERE c.grade < 300 
ORDER BY c.customer_id;
```

**Output:**

<img width="1297" height="610" alt="image" src="https://github.com/user-attachments/assets/575dbd84-866b-410a-b628-61f1f4ad991c" />


**Question 2**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman_id values that have more than one associated customer.

```sql
SELECT 
    s.name, 
    c.cust_name, 
    c.city, 
    c.grade, 
    c.salesman_id
FROM salesman s
LEFT JOIN customer c 
    ON s.salesman_id = c.salesman_id
WHERE s.salesman_id IN (
    SELECT salesman_id
    FROM customer
    GROUP BY salesman_id
    HAVING COUNT(*) > 1
);
```

**Output:**

<img width="1291" height="491" alt="image" src="https://github.com/user-attachments/assets/44b15ae9-b749-4ca7-af7a-d038f37b61b8" />


**Question 3**
---
Write the SQL query that achieves the selection of admission dates from the "patients" table and surgery dates from the "surgeries" table, with an inner join on the "patient_id" column.

```sql
SELECT p.admission_date , s.surgery_date
FROM PATIENTS p
INNER JOIN SURGERIES s
ON p.patient_id = s.patient_id;
```

**Output:**

<img width="1213" height="582" alt="image" src="https://github.com/user-attachments/assets/f88f6da3-2952-4017-8f3e-cf2bb6467ece" />


**Question 4**
---
Write the SQL query that achieves the selection of the first name from the "patients" table, with an inner join on the "patient_id" column and a condition filtering for surgeries with a surgery date of '2024-01-15'.:

```sql
SELECT p.first_name FROM PATIENTS p
INNER JOIN SURGERIES s
ON p.patient_id = s.patient_id
WHERE surgery_date = '2024-01-15';
```

**Output:**

<img width="1217" height="420" alt="image" src="https://github.com/user-attachments/assets/fcc0aacd-6184-42eb-9845-6f932b15abfd" />


**Question 5**
---
Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.

```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt as "Order Amount"
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
ORDER BY o.ord_date ASC;
```

**Output:**

<img width="1290" height="963" alt="image" src="https://github.com/user-attachments/assets/6f893e0e-a1eb-4fe9-b73c-60f7f96fd1e7" />


**Question 6**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

```sql
SELECT o.ord_no,o.purch_amt,c.cust_name,c.city
FROM orders o
INNER join customer c
ON o.customer_id = c.customer_id
WHERE purch_amt between 500 and 2000;
```

**Output:**

<img width="1260" height="423" alt="image" src="https://github.com/user-attachments/assets/48158741-f213-4384-a77f-ea3ea6816163" />


**Question 7**
---
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

```sql
SELECT s.name as Salesman, c.cust_name,c.city
FROM Salesman s
INNER JOIN customer c
ON s.city = c.city;
```

**Output:**

<img width="1210" height="734" alt="image" src="https://github.com/user-attachments/assets/dffcab77-b4c8-4f41-a33d-89693148d351" />


**Question 8**
---
Write an SQL query to retrieve all columns from the 'customer' table (aliased as 'c') using a LEFT JOIN with the 'orders' table on the 'customer_id' column, and filter the results to include only those orders placed between '2012-07-01' and '2012-07-30'.

```sql
SELECT 
    c.*
FROM customer c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
WHERE o.ord_date BETWEEN '2012-07-01' AND '2012-07-30';
```

**Output:**

<img width="1292" height="309" alt="image" src="https://github.com/user-attachments/assets/7349713b-cff3-4992-86db-8bc3c6a82336" />


**Question 9**
---
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

```sql
SELECT c.cust_name, c.city, c.grade,s.name as Salesman, s.city
FROM customer c
INNER JOIN salesman s
ON 
c.salesman_id = s.salesman_id
ORDER BY c.customer_id ASC;
```

**Output:**

<img width="1297" height="722" alt="image" src="https://github.com/user-attachments/assets/ae2e4078-8852-4d78-99a2-f75d18d0f0f6" />


**Question 10**
---
Write the SQL query that accomplishes the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a non-null discharge date.

```sql
SELECT p.first_name as patient_name, d.first_name as doctor_name
FROM PATIENTS p
INNER JOIN
DOCTORS d
ON p.doctor_id = d.doctor_id
WHERE p.discharge_date IS NOT NULL;
```

**Output:**

`<img width="1058" height="518" alt="image" src="https://github.com/user-attachments/assets/0667c781-4bea-4f77-a8a3-bebbb03bce54" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
