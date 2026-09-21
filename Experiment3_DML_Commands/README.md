# Experiment 3: DML Commands

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

Products table

product_id product_name category cost_price sell_price reorder_lvl quantity supplier_id

```
UPDATE products
SET  product_name = 'Premium Bread'
WHERE product_id = 5;
```

**Output:**

<img width="838" height="306" alt="image" src="https://github.com/user-attachments/assets/f275bf12-4e00-4b76-b183-93bbd7812816" />


**Question 2**
For Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

PRODUCTS TABLE

name type

product_id INT product_name VARCHAR(100) category VARCHAR(50) cost_price DECIMAL(10,2) sell_price DECIMAL(10,2) reorder_lvl INT quantity INT supplier_id INT

SALES TABLE name type

sale_id INT sale_date DATE product_id INT quantity INT sell_price DECIMAL(10,2) total_sell_price DECIMAL(10,2)
```
UPDATE sales 
set sell_price = sell_price + 3
where product_id IN (
    select product_id
    from products
    where supplier_id = 4
);
```
**Output:**

<img width="833" height="282" alt="image" src="https://github.com/user-attachments/assets/41b5b880-0293-4822-85f7-8e734709cf10" />


**Question 3**

Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

Employees table

employee_id first_name last_name email phone_number hire_date job_id salary commission_pct manager_id department_id
```
update employees
set first_name = 'John'
where department_id = 80 and commission_pct < 0.35;
```
**Output:**

<img width="836" height="385" alt="image" src="https://github.com/user-attachments/assets/71f0dff3-836c-4a47-a2f1-765a4addea3d" />


**Question 4**
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

name type

supplier_id INT supplier_name VARCHAR(100) contact_person VARCHAR(100) phone_number VARCHAR(20) email VARCHAR(100) address VARCHAR(250)
```
update suppliers
set supplier_name = upper(supplier_name)
where contact_person like '%Singh%';
```
**Output:**

<img width="836" height="258" alt="image" src="https://github.com/user-attachments/assets/bbff1ff9-a751-4472-8d18-47a012a350fb" />


**Question 5**

Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.

Employees table

employee_id first_name last_name email phone_number hire_date job_id salary commission_pct manager_id department_id
```
update employees
set email = 'Unavailable'
```
**Output:**

<img width="832" height="312" alt="image" src="https://github.com/user-attachments/assets/2c98e2ca-ecb8-476b-9700-e15f5fd81b41" />


**Question 6**

Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' has exactly 6 characters.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
|CUST_CODE | CUST_NAME | CUST_CITY | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO | AGENT_CODE | +-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+ | C00013 | Holmes | London | London | UK | 2 | 6000.00 | 5000.00 | 7000.00 | 4000.00 | BBBBBBB | A003 | | C00001 | Micheal | New York | New York | USA | 2 | 3000.00 | 5000.00 | 2000.00 | 6000.00 | CCCCCCC | A008 | | C00020 | Albert | New York | New York | USA | 3 | 5000.00 | 7000.00 | 6000.00 | 6000.00 | BBBBSBB | A008 |
```
delete from Customer
where LENGTH(CUST_NAME)=6;
```
**Output:**

<img width="836" height="482" alt="image" src="https://github.com/user-attachments/assets/ef008a0f-652f-4066-bb7d-a94776dc651b" />


**Question 7**
 Write a SQL query to Delete customers with 'GRADE' 2 and 'CUST_NAME' starting with 'M', and whose 'PAYMENT_AMT' is less than 3000

Sample table: Customer
```
delete from Customer
where (GRADE=2 or CUST_NAME='M')
and PAYMENT_AMT < 3000;
```
**Output:**

<img width="838" height="307" alt="image" src="https://github.com/user-attachments/assets/8c41330b-4df1-4ea3-9c3e-dc96d11ee816" />


**Question 8**

Write a SQL query to remove rows from the table 'customer' with the following condition -

'cust_country' must be 'India',

'cus_city' must not be 'Chennai',

Sample table: Customer
```
delete from customer
where cust_country = 'India'
    and cust_city != 'Chennai';
```
**Output:**

<img width="837" height="542" alt="image" src="https://github.com/user-attachments/assets/2662c163-50d5-4705-a02f-a6045752c0d0" />


**Question 9**

Write a SQL query to Delete customers from 'customer' table where 'OPENING_AMT' is between 4000 and 6000.

Sample table: Customer
```
delete from Customer
where OPENING_AMT between 4000 and 6000;
```
**Output:**

<img width="837" height="411" alt="image" src="https://github.com/user-attachments/assets/4f3b519e-3653-4c89-926a-727890b3d6ea" />


**Question 10**
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is greater than or equal to 2.

Sample table: Customer
```
delete from Customer
where GRADE >= 2;
```
**Output:**

<img width="837" height="701" alt="image" src="https://github.com/user-attachments/assets/db5a3ea9-dc17-4a30-a23d-20cb1c02cf33" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
