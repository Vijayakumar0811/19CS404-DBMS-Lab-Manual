# Experiment 2: DDL Commands
## NAME: VIJAYAKUMAR S
## REG NO: 212224040359

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
-- Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.

```sql
CREATE TABLE Department(
    DepartmentID INTEGER PRIMARY KEY,
    DepartmentName TEXT UNIQUE NOT NULL,
    Location TEXT
);
```

**Output:**
<img width="1163" height="299" alt="image" src="https://github.com/user-attachments/assets/7c46ff7c-49c2-4155-9b57-1b4164384ed4" />


**Question 2**
---
Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

```sql
INSERT INTO Employee(EmployeeID, Name, Position, Department, Salary) VALUES
(001,'Sarah Parker','Manager','HR',60000);
```

**Output:**

<img width="1156" height="252" alt="image" src="https://github.com/user-attachments/assets/c4374eaa-37b2-4979-9101-4f35d126cba0" />


**Question 3**
---
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

```sql
INSERT INTO Employee(EmployeeID, Name, Department, Salary)
SELECT EmployeeID, Name, Department, Salary
FROM Former_employees;
```

**Output:**

<img width="1161" height="304" alt="image" src="https://github.com/user-attachments/assets/4fbb64f2-3185-4ee6-ac63-4198be3c4f7d" />


**Question 4**
---
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
CREATE TABLE Orders(
    OrderID INTEGER PRIMARY KEY,
    OrderDate Date not null,
    CustomerID Integer,
    Foreign key (CustomerID) REFERENCES Customers(CustomerID)
);
```

**Output:**

<img width="1160" height="303" alt="image" src="https://github.com/user-attachments/assets/788165f6-6242-4cd9-bcc5-841d5139605b" />


**Question 5**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
CREATE TABLE ProjectAssignments(
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER, 
    AssignmentDate DATE NOT NULL ,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);
```

**Output:**

<img width="1157" height="300" alt="image" src="https://github.com/user-attachments/assets/054bae8f-abc0-4c37-bcdb-bafd67053c6a" />


**Question 6**
---
Write a SQL query to add a column named Date_of_birth as Date in the Student_details table.

```sql
ALTER TABLE Student_details
ADD COLUMN Date_of_birth Date;
```

**Output:**

<img width="1157" height="383" alt="image" src="https://github.com/user-attachments/assets/746a1626-0c07-4704-9352-5b98f724ce69" />


**Question 7**
---
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.

```sql
CREATE TABLE Bonuses(
    BonusID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    BonusAmount REAL CHECK (BonusAmount > 0),
    BonusDate DATE,
    Reason TEXT NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1161" height="298" alt="image" src="https://github.com/user-attachments/assets/b92fd76b-fcdb-4a2b-b4c4-e98fd186716c" />


**Question 8**
---
Insert the following students into the Student_details table:

| RollNo | Name        | Gender | Subject     | Marks |
|-------:|-------------|:------:|-------------|------:|
| 202    | Ella King   | F      | Chemistry   | 87    |
| 203    | James Bond  | M      | Literature  | 78    |

```sql
INSERT INTO Student_details(RollNo, Name, Gender, Subject,MARKS) VALUES
(202,'Ella King','F','Chemistry',87),
(203,'James Bond','M','Literature',78);
```

**Output:**

<img width="1157" height="280" alt="image" src="https://github.com/user-attachments/assets/f9f3f640-341f-4b22-8709-32067a642760" />


**Question 9**
---
Create a table named Tasks with the following columns:

TaskID as INTEGER
TaskName as TEXT
DueDate as DATE
```sql
CREATE TABLE Tasks(
    TaskID INTEGER,
    TaskName TEXT,
    DueDate DATE
);
```

**Output:**

<img width="1157" height="395" alt="image" src="https://github.com/user-attachments/assets/76766d35-6b9a-4bc0-a4f8-814adb748078" />


**Question 10**
---
Write a SQL Query to add an attribute designation in the employee table with the data type VARCHAR(50).


```sql
ALTER TABLE employee
ADD COLUMN designation varchar(50);
```

**Output:**

<img width="1157" height="302" alt="image" src="https://github.com/user-attachments/assets/ddbae381-e131-4006-8639-f41a9c90d41e" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
