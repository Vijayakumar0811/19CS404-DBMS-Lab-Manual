# Experiment 4: Aggregate Functions, Group By and Having Clause

## NAME: VIJAYAKUMAR S

## REG NO: 212224040359

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
How many medical records are there for each patient?

```sql
SELECT PatientID, count(RecordID) as TotalRecords from MedicalRecords
Group By PatientID;
```

**Output:**

<img width="1156" height="698" alt="image" src="https://github.com/user-attachments/assets/68e96509-d07c-4e92-97d0-4fde6ea6a0e5" />

**Question 2**
---
What is the count of male and female patients?

```sql
Select Gender, Count(Gender) as TotalPatients
 from Patients
group by Gender;
```

**Output:**

<img width="1144" height="377" alt="image" src="https://github.com/user-attachments/assets/4a434fee-b4cf-4ec9-9d99-43c85fdbb343" />

**Question 3**
How many prescriptions were written for each medication?

```sql
SELECT Medication, count(Medication) as TotalPrescriptions 
from Prescriptions group by Medication;
```

**Output:**

<img width="1149" height="801" alt="image" src="https://github.com/user-attachments/assets/5777284e-7b74-4a62-bbcd-56282da3be05" />

**Question 4**
---
Write a SQL query to find the total amount of fruits with a unit type of 'LB'.

Note: Inventory attribute contains amount of fruits
```sql
SELECT sum(inventory) as total from fruits where unit = 'LB' ;
```

**Output:**

<img width="1150" height="324" alt="image" src="https://github.com/user-attachments/assets/b54d831c-55ef-4592-ac1c-94cf13ba3559" />

**Question 5**
---
Write a SQL query to  find the average salary of all employees?
```sql
Select avg(income) as Average_Salary from employee;
```

**Output:**

<img width="1150" height="325" alt="image" src="https://github.com/user-attachments/assets/d6794498-aecf-4cec-a625-ee3c4e3d1732" />

**Question 6**
---
Write a SQL query to determine the number of customers who received at least one grade for their activity.


```sql
Select COUNT(customer_id) as COUNT from customer
 where grade >= 1;
```

**Output:**

<img width="1148" height="322" alt="image" src="https://github.com/user-attachments/assets/6a5f4dcb-b3fe-464e-a59a-6732546dfa6e" />

**Question 7**
---
Write a SQL query to find the shortest email address in the customer table?


```sql
Select name , email, Length(email) as min_email_length 
from customer
order by Length(email) limit 1;
```

**Output:**

<img width="1147" height="324" alt="image" src="https://github.com/user-attachments/assets/e1efc647-64b2-40d7-bc9b-d226b8aa1076" />

**Question 8**
---
Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 400,000.

```sql
Select age, MIN(income) from employee
group by age
having min(income) < 400000;
```

**Output:**

<img width="1149" height="397" alt="image" src="https://github.com/user-attachments/assets/b1b74a08-ae89-4412-bb88-2038bb8128de" />

**Question 9**
---
Write the SQL query that achieves the selection of category and calculates the sum of the product of price and category ID as Revenue for each category from the "products" table, and includes only those products where the total revenue is greater than 25.

```sql
SELECT category_id , sum(price*category_id) as Revenue 
from products 
group by category_id
having Revenue > 25;
```

**Output:**

<img width="1145" height="456" alt="image" src="https://github.com/user-attachments/assets/8207a89f-ee3a-48b3-99a3-089016591605" />

**Question 10**
---
Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.

```sql
SELECT city, AVG(income) from employee
group by city
having AVG(income) > 500000;
```

**Output:**

<img width="1148" height="455" alt="image" src="https://github.com/user-attachments/assets/42e359cb-6922-4234-a903-25f29b7e6633" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
