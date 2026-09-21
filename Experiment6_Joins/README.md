# Experiment 6: Joins

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

Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id
```
SELECT p.first_name AS patient_name, t.*
FROM patients AS p
INNER JOIN test_results AS t
ON p.patient_id = t.patient_id
WHERE t.test_name = 'Blood Pressure';
```
**Output:**

<img width="807" height="268" alt="image" src="https://github.com/user-attachments/assets/7f3f010e-3a43-4613-9a71-3f89fa6ad80f" />

**Question 2**

 write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

Sample table: salesman
```
SELECT s.name AS Salesman,
       c.cust_name,
       s.city
FROM salesman s
JOIN customer c
ON s.city = c.city;
```
**Output:**

<img width="795" height="578" alt="image" src="https://github.com/user-attachments/assets/587878d1-21a9-4a75-9b7d-489151afadb1" />

**Question 3**

SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.

Sample table: customer
```
SELECT c.cust_name,
       c.city,
       o.ord_no,
       o.ord_date,
       o.purch_amt AS "Order Amount",
       s.name,
       s.commission
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
LEFT JOIN salesman s
ON c.salesman_id = s.salesman_id;
```
**Output:**

<img width="805" height="435" alt="image" src="https://github.com/user-attachments/assets/f8046905-9ccd-4ca0-be5e-e17da57fa31e" />

**Question 4**

From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission.

Sample table: orders
```
SELECT o.ord_no,
       o.ord_date,
       o.purch_amt,
       c.cust_name AS "Customer Name",
       c.grade,
       s.name AS "Salesman",
       s.commission
FROM orders o
JOIN customer c
    ON o.customer_id = c.customer_id
JOIN salesman s
    ON o.salesman_id = s.salesman_id;
```
**Output:**


<img width="795" height="497" alt="image" src="https://github.com/user-attachments/assets/26cdd3ac-353d-463a-ae45-f608e272b738" />

**Question 5**
 From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.

Sample table: customer
```
SELECT c.cust_name,
       c.city,
       c.grade,
       s.name AS Salesman,
       s.city
FROM customer c
JOIN salesman s
    ON c.salesman_id = s.salesman_id
ORDER BY c.customer_id ASC;
```
**Output:**

<img width="812" height="522" alt="image" src="https://github.com/user-attachments/assets/fcb0d5b6-b2d8-4a39-93b8-3ac5a8aafe7c" />

**Question 6**

Write the SQL query that achieves the selection of all columns from the "patients" table, with an inner join on the "doctor_id" column, and includes a condition filtering for patients whose doctors have the first name 'John' and last name 'Smith'.

PATIENTS TABLE:

```
SELECT p.*
FROM patients p
INNER JOIN doctors d
    ON p.doctor_id = d.doctor_id
WHERE d.first_name = 'John'
  AND d.last_name = 'Smith';
```
**Output:**

<img width="806" height="295" alt="image" src="https://github.com/user-attachments/assets/3044e5be-fe2d-4c39-8f80-cc86ad06a157" />

**Question 7**

From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

Sample table: customer

```
SELECT c.cust_name AS "Customer Name",
       c.city,
       s.name AS Salesman,
       s.commission
FROM customer c
INNER JOIN salesman s
    ON c.salesman_id = s.salesman_id;
```
**Output:**

<img width="812" height="510" alt="image" src="https://github.com/user-attachments/assets/9a45a6b2-a143-4017-ad1b-4f9b74a6443c" />

**Question 8**
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman_id values that have more than one associated customer.

Customer Table: (customer_id, cust_name, city, grade, salesman_id)

Salesman Table: (salesman_id, name, city, commission)

```
SELECT s.name,
       c.cust_name,
       c.city,
       c.grade,
       c.salesman_id
FROM salesman s
LEFT JOIN customer c ON s.salesman_id = c.salesman_id
WHERE c.salesman_id IN (
    SELECT salesman_id
    FROM customer
    GROUP BY salesman_id
    HAVING COUNT(*) > 1
)
ORDER BY c.salesman_id, c.customer_id;
```

**Output:**

<img width="807" height="405" alt="image" src="https://github.com/user-attachments/assets/8af1cc62-25b4-498e-b45b-26cdbfbea13f" />

**Question 9**

Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)
```
SELECT c.cust_name,
       o.ord_no,
       o.ord_date,
       o.purch_amt
FROM customer AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id;
```

**Output:**
<img width="802" height="437" alt="image" src="https://github.com/user-attachments/assets/81adda79-e610-4028-abd0-7a03588fe8b9" />


**Question 10**

Write the SQL query that achieves the selection of all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id
```
SELECT t.*
FROM test_results AS t
INNER JOIN patients AS p
    ON t.patient_id = p.patient_id
WHERE p.first_name = 'Alice';
```

**Output:**

<img width="806" height="268" alt="image" src="https://github.com/user-attachments/assets/1c4e797c-6f43-4288-9f3e-ca776c219b87" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
