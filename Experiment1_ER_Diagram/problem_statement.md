# ER Diagram Workshop – Submission Template

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

<img width="932" height="547" alt="image" src="https://github.com/user-attachments/assets/a4e0ab7d-0506-4ea5-bca2-cfb2e6b7e15d" />


### Entities and Attributes

<img width="938" height="553" alt="image" src="https://github.com/user-attachments/assets/e37ba0f1-b72d-49cd-bf8c-daad582aebc0" />



### Relationships and Constraints

<img width="932" height="577" alt="image" src="https://github.com/user-attachments/assets/99b5c63c-601c-4b43-adc5-7dc1be9cd718" />


### Assumptions

Every trainer can teach one or more programs. Members may join multiple fitness programs. Attendance is recorded for every session Payments are made only by registered members.

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

<img width="837" height="465" alt="image" src="https://github.com/user-attachments/assets/94426701-9df1-41dd-be2a-157aa5ff627e" />


### Entities and Attributes

<img width="840" height="328" alt="image" src="https://github.com/user-attachments/assets/814da702-a2f4-4d47-ba80-2a8e96fb7007" />



### Relationships and Constraints

<img width="837" height="347" alt="image" src="https://github.com/user-attachments/assets/a4b5fd43-1199-4ddf-9a7c-ddac5fbfa315" />


### Assumptions

Only registered members can borrow books. Members may register for multiple events. Every event has at least one speaker. A book can be borrowed many times at different periods.

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

<img width="830" height="465" alt="image" src="https://github.com/user-attachments/assets/7421fe86-c234-49b7-baf6-87accb7b76d2" />

### Entities and Attributes

<img width="842" height="357" alt="image" src="https://github.com/user-attachments/assets/f84b1c87-c9fd-4961-ac34-319b81f37c6c" />


### Relationships and Constraints

<img width="837" height="335" alt="image" src="https://github.com/user-attachments/assets/9141b60e-70b3-41fa-bd0f-cad9aba44f02" />


### Assumptions

Only customers can make reservations. Every reservation is served by one waiter Multiple dishes can be included in a single order.


## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
