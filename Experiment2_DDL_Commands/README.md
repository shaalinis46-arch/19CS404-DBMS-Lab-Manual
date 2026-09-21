# Experiment 2: DDL Commands

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

Write an SQL query to add two new columns, first_name and last_name, to the table employee. Both columns should have a data type of varchar(50).

```
ALTER TABLE employee ADD first_name varchar(50);
ALTER TABLE employee ADD last_name varchar(50);
```

**Output:**
<img width="935" height="232" alt="image" src="https://github.com/user-attachments/assets/5eaec147-beaa-4f3e-89bc-9509a837e884" />


**Question 2**

Create a table named Shipments with the following constraints: ShipmentID as INTEGER should be the primary key. ShipmentDate as DATE. SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID). OrderID as INTEGER should be a foreign key referencing Orders(OrderID).


```
CREATE TABLE Shipments(
ShipmentID INTEGER primary key,
ShipmentDate DATE,
SupplierID INTEGER, 
OrderID INTEGER,
foreign key  (SupplierID) REFERENCES Suppliers(SupplierID),
foreign key (OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**
<img width="932" height="223" alt="image" src="https://github.com/user-attachments/assets/f482a92d-cf79-45b2-a178-d85fc01cebac" />


**Question 3**

Insert all students from Archived_students table into the Student_details table.

cid name type notnull dflt_value pk

0 RollNo INT 0 1 1 Name VARCHAR(100) 0 0 2 Gender VARCHAR(10) 0 0 3 Subject VARCHAR(50) 0 0 4 MARKS INT 0 0

```
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
select RollNo,Name,Gender,Subject,MARKS
from Archived_students;
```

**Output:**
<img width="932" height="262" alt="image" src="https://github.com/user-attachments/assets/767d0e11-5f02-498c-b5d0-c7d5d0635278" />


**Question 4**

In the Cusomers table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

CustomerID Name Address City ZipCode

306 Diana Prince Themyscira 307 Bruce Wayne Wayne Manor Gotham 10007 308 Peter Parker Queens 11375

```
INSERT INTO Customers (CustomerID, Name, Address)
VALUES (306, 'Diana Prince', 'Themyscira');
INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode)
VALUES (307, 'Bruce Wayne', 'Wayne Mano', 'Gotham', '10007');
INSERT INTO Customers (CustomerID, Name, Address, ZipCode)
VALUES (308, 'Peter Parker', 'Queens', '11375');
```

**Output:**
<img width="932" height="265" alt="image" src="https://github.com/user-attachments/assets/905e152b-38d3-4b70-a832-b1db188fa1da" />


**Question 5**

Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.

Sample table: customer

customer_id | cust_name | city | grade | salesman_id -------------+----------------+------------+-------+------------- 3002 | Nick Rimando | New York | 100 | 5001 3007 | Brad Davis | New York | 200 | 5001 3005 | Graham Zusi | California | 200 | 5002

```
ALTER TABLE customer ADD discount DECIMAL(5,2);
```


**Output:**

<img width="935" height="325" alt="image" src="https://github.com/user-attachments/assets/cdcaafcd-09a6-4183-a582-423ac9ef3300" />


**Question 6**

Create a new table named contacts with the following specifications: contact_id as INTEGER and primary key. first_name as TEXT and not NULL. last_name as TEXT and not NULL. email as TEXT. phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```
CREATE TABLE contacts(
contact_id INTEGER primary key,
first_name TEXT not NULL,
last_name TEXT not NULL,
email TEXT,
phone TEXT not NULL CHECK (LENGTH (PHONE) >= 10)
);
```

**Output:**
<img width="931" height="307" alt="image" src="https://github.com/user-attachments/assets/30bebb06-6b98-4e05-8134-a1a193ac3540" />


**Question 7**

Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.

RollNo Name Gender

204 Samuel Black M

Note: The Subject and MARKS columns will use their default values.


```
INSERT INTO Student_details(RollNo,Name, Gender)
VALUES (204,'Samuel Black' ,'M');
```

**Output:**

<img width="931" height="295" alt="image" src="https://github.com/user-attachments/assets/3bde2f76-e245-4f78-83d7-b867d244b2de" />


**Question 8**

Create a table named Invoices with the following constraints: InvoiceID as INTEGER should be the primary key. InvoiceDate as DATE. Amount as REAL should be greater than 0. DueDate as DATE should be greater than the InvoiceDate. OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```
CREATE TABLE Invoices(
InvoiceID INTEGER primary key,
InvoiceDate DATE,
Amount REAL CHECK (Amount>0),
DueDate DATE CHECK (DueDate > InvoiceDate),
OrderID INTEGER,
foreign key (OrderID) references Orders(OrderID)
);
```

**Output:**
<img width="840" height="241" alt="image" src="https://github.com/user-attachments/assets/00c53b3d-8561-464b-acca-79c2b8161ca5" />


**Question 9**

Create a new table named products with the following specifications: product_id as INTEGER and primary key. product_name as TEXT and not NULL. list_price as DECIMAL (10, 2) and not NULL. discount as DECIMAL (10, 2) with a default value of 0 and not NULL. A CHECK constraint at the table level to ensure: list_price is greater than or equal to discount discount is greater than or equal to 0 list_price is greater than or equal to 0

```
CREATE TABLE products(
product_id INTEGER primary key,
product_name TEXT not NULL,
list_price DECIMAL (10, 2) not NULL,
discount DECIMAL (10, 2) DEFAULT 0 NOT NULL,
CHECK (list_price  >= discount AND discount >=0 AND list_price >=0)
);
```
**Output:**


<img width="840" height="223" alt="Screenshot 2026-09-21 132120" src="https://github.com/user-attachments/assets/2be05721-8737-4c74-afbc-9b174e013b6b" />


**Question 10**

Create a table named Customers with the following columns:

CustomerID as INTEGER Name as TEXT Email as TEXT JoinDate as DATETIME

```
CREATE TABLE Customers(
CustomerID INTEGER,
Name TEXT,
Email TEXT,
JoinDate DATETIME
);
```

**Output:**

<img width="836" height="290" alt="image" src="https://github.com/user-attachments/assets/dc1bde82-eea3-4986-a415-175c54ad911a" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
