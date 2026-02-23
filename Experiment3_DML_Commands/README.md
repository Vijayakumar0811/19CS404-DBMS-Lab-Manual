# Experiment 3: DML Commands
## NAME: VIJAYAKUMAR S
## REG NO: 212224040359
## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

```sql
UPDATE products
SET product_name = 'Premium Bread' WHERE product_id = 5;
```

**Output:**

<img width="1187" height="383" alt="image" src="https://github.com/user-attachments/assets/3de770f0-fc55-439e-8572-b4388a9bb835" />


**Question 2**
---
Write a SQL statement to Update the reorder level to 20 where the quantity in stock is less than 10 and product category is 'Snacks' in the products table.

```sql
UPDATE products
SET reorder_lvl = 20
WHERE quantity < 10
AND category = 'Snacks';
```

**Output:**
<img width="1186" height="549" alt="image" src="https://github.com/user-attachments/assets/af793d93-6f4b-4289-9a6a-52a3a86fa3ea" />


**Question 3**
---
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

```sql
UPDATE Products
SET sell_price = sell_price * 1.10
WHERE category = 'Bakery';
```

**Output:**

<img width="1191" height="502" alt="image" src="https://github.com/user-attachments/assets/c750da8d-af04-4f4f-9cf3-60c92b5a6c85" />


**Question 4**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'

```sql
UPDATE Employees
SET salary = salary * 2
WHERE job_id LIKE '%MAN';
```

**Output:**

<img width="1191" height="339" alt="image" src="https://github.com/user-attachments/assets/f7ab1825-6c2a-49d9-888b-e171352c887a" />


**Question 5**
---
Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

```sql
UPDATE SALES
SET sell_price = sell_price + 3
WHERE product_id IN (SELECT product_id FROM products
WHERE supplier_id = 4);
```

**Output:**

<img width="1191" height="357" alt="image" src="https://github.com/user-attachments/assets/090161ba-72e3-46e1-a93d-271251237bb8" />


**Question 6**
---
Write a SQL query to Delete customers with following conditions

   1.'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada')

   2.'GRADE' is greater than or equal to 3

```sql
DELETE FROM Customer WHERE
 CUST_COUNTRY NOT IN ('UK','USA','Canada')
AND GRADE >= 3;
```

**Output:**

<img width="1190" height="407" alt="image" src="https://github.com/user-attachments/assets/e6468dbb-27d0-4c26-b3ca-310d8361507a" />


**Question 7**
---
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.



```sql
DELETE FROM Doctors WHERE doctor_id = 1;
```

**Output:**

<img width="1195" height="256" alt="image" src="https://github.com/user-attachments/assets/3819535d-bce6-4156-833b-d73e6d28f210" />


**Question 8**
---
Show the categoryName and description from the categories table sorted by categoryName.

```sql
SELECT categoryName, description FROM categories
 ORDER BY categoryName;
```

**Output:**

<img width="1155" height="586" alt="image" src="https://github.com/user-attachments/assets/f4ed5726-04e2-4cbc-accb-67d84d92647d" />


**Question 9**
---
Write a SQL query to Select all patients who were admitted during the year 2023.



```sql
SELECT patient_id, first_name, admission_date FROM Patients
WHERE admission_date BETWEEN '2023-01-01' AND '2023-12-31';
```

**Output:**

<img width="1154" height="351" alt="image" src="https://github.com/user-attachments/assets/bf3a18e2-71a0-4956-82b7-032e5e284b81" />


**Question 10**
---
Write a SQL query to assess the performance of value2 as 'Poor', 'Average', or 'Excellent' based on whether it is less than 30, between 30 and 70, or greater than 70 in the Calculations table

```sql
SELECT 
    id,
    value2,
    CASE
        WHEN value2 < 30 THEN 'Poor'
        WHEN value2 BETWEEN 30 AND 70 THEN 'Average'
        ELSE 'Excellent'
    END AS performance
FROM Calculations;
```

**Output:**

<img width="1151" height="458" alt="image" src="https://github.com/user-attachments/assets/de142e3e-cd34-4b47-91be-59d41d5e25db" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
