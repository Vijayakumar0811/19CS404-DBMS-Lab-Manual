# Experiment 9: PL/SQL – Procedures and Functions
## NAME: VIJAYAKUMAR S
## REG NO: 212224040359
## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.

### PROGRAM: 
```
CREATE OR REPLACE PROCEDURE find_square(n NUMBER)
IS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Square of ' || n || ' is ' || (n*n));
END;
/
```

**Expected Output:**  
Square of 6 is 36

### OUTPUT:
<img width="479" height="210" alt="image" src="https://github.com/user-attachments/assets/4df966fb-c822-4857-b984-3892e58f7247" />

---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

### PROGRAM:
```
CREATE OR REPLACE FUNCTION get_factorial(n NUMBER)
RETURN NUMBER
IS
    fact NUMBER := 1;
    i NUMBER := 1;
BEGIN
    WHILE i <= n LOOP
        fact := fact * i;
        i := i + 1;
    END LOOP;

    RETURN fact;
END;
/
```

**Expected Output:**  
Factorial of 5 is 120

### OUTPUT:
<img width="416" height="187" alt="image" src="https://github.com/user-attachments/assets/be1a663e-b61e-415a-8cd0-ede3c4816bcc" />

---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

### PROGRAM:
```
CREATE OR REPLACE PROCEDURE check_even_odd(n NUMBER)
IS
BEGIN
    IF MOD(n,2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(n || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(n || ' is Odd');
    END IF;
END;
/
```

**Expected Output:**  
12 is Even

### OUTPUT:
<img width="429" height="221" alt="image" src="https://github.com/user-attachments/assets/addfb4f9-d7cd-474d-a38a-747ddfb123de" />

---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

### PROGRAM:
```
CREATE OR REPLACE FUNCTION reverse_number(n NUMBER)
RETURN NUMBER
IS
    rev NUMBER := 0;
    temp NUMBER := n;
    rem NUMBER;
BEGIN
    WHILE temp > 0 LOOP
        rem := MOD(temp,10);
        rev := rev * 10 + rem;
        temp := FLOOR(temp/10);
    END LOOP;

    RETURN rev;
END;
/
```
**Expected Output:**  
Reversed number of 1234 is 4321

### OUTPUT:
<img width="503" height="170" alt="image" src="https://github.com/user-attachments/assets/56f7ef49-c8c7-491e-aeb8-337346b7a396" />


---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

### PROGRAM:
```
CREATE OR REPLACE PROCEDURE print_table(n NUMBER)
IS
    i NUMBER := 1;
BEGIN
    WHILE i <= 10 LOOP
        DBMS_OUTPUT.PUT_LINE(n || ' x ' || i || ' = ' || (n*i));
        i := i + 1;
    END LOOP;
END;
/
```

**Expected Output:**  
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50
### OUTPUT:
<img width="445" height="390" alt="image" src="https://github.com/user-attachments/assets/50565089-14f5-47e5-91d8-0d68b2cca3d0" />

## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
