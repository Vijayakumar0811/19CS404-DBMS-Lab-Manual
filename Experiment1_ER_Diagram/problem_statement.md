# ER Diagram Workshop – Submission Template
## NAME: VIJAYAKUMAR S
## REG NO: 212224040359

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:

![ER Diagram]<img width="1070" height="548" alt="image" src="https://github.com/user-attachments/assets/18f40c8e-040d-451a-85d9-567868a915e9" />


### Entities and Attributes


| Entity       | Attributes (PK, FK)                                                    | Notes                                     |
| ------------ | ---------------------------------------------------------------------- | ----------------------------------------- |
|   Trainer    |   Trainer_ID (PK)  , Trainer_Name, Phone, Specialization               | One trainer can conduct multiple sessions |
|   Members    |   Member_ID (PK)  , Name, Phone_No, Member_Type, Start_Date            | Members attend sessions and make payments |
|   Session    |   Session_ID (PK)  , Date, Time, Duration, Attendance, Trainer_ID (FK) | Conducted by one trainer                  |
|   Programs   |   Program_ID (PK)  , Program_Name, Fee                                 | Members join programs                     |
|   Payment    |   Payment_ID (PK)  , Payment_Date, Amount, Member_ID (FK)              | Each payment belongs to one member        |


### Relationships and Constraints

| Relationship                   | Cardinality | Participation    | Notes                                 |
| ------------------------------ | ----------- | ---------------- | ------------------------------------- |
|   Training   (Trainer–Members) | 1 : M       | Partial          | One trainer trains many members       |
|   Conducts   (Trainer–Session) | 1 : M       | Total on Session | Each session must have one trainer    |
|   Attends   (Members–Session)  | M : N       | Partial          | A member can attend many sessions     |
|   Joins   (Members–Programs)   | M : 1       | Total on Members | Each member joins one program         |
|   Does   (Members–Payment)     | 1 : M       | Total on Payment | One member can make multiple payments |


### Assumptions
Each Member has a unique Member_ID and can join only one program at a time.

Each Trainer has a unique Trainer_ID and can conduct multiple sessions.

Every Session is conducted by only one trainer.

A Member can attend multiple sessions, and a session can have multiple members.

Each Payment is made by one member, but a member can make multiple payments.

Program fee is fixed and defined in the Programs entity.

Phone numbers are assumed to be unique for trainers and members.

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
