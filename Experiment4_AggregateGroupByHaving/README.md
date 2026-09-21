# Experiment 4: Aggregate Functions, Group By and Having Clause

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

What is the average dosage prescribed for each medication?

Sample tablePrescriptions Table

```
select
    Medication,
    AVG(Dosage) AS AvgDosage
from Prescriptions
group by Medication;
```
**Output:**
<img width="855" height="897" alt="image" src="https://github.com/user-attachments/assets/47f985f0-069f-4803-8e65-90995c8eba2d" />


**Question 2**

What is the total number of appointments scheduled by each doctor?

Sample table:Appointments Table

```
select DoctorID, count(*) as TotalAppointments
from Appointments
group by DoctorID;
```

**Output:**

<img width="870" height="787" alt="image" src="https://github.com/user-attachments/assets/2cae494f-f253-4716-b45d-54743967b173" />


**Question 3**

How many appointments are scheduled for each doctor?

Sample table:Appointments Table

```
select DoctorID, count(*) as TotalAppointments
from Appointments
group by DoctorID;
```

**Output:**

<img width="828" height="765" alt="image" src="https://github.com/user-attachments/assets/1e9e0bc2-0e25-4384-a3e3-5ec2e3771e7e" />


**Question 4**
Write a SQL query to find the average length of email addresses (in characters):

Table: customer

name type

id INTEGER name TEXT city TEXT email TEXT phone INTEGER

```
select AVG(LENGTH(email)) AS avg_email_length
from customer;
```

**Output:**
<img width="705" height="440" alt="image" src="https://github.com/user-attachments/assets/eb3b2e82-9848-4606-aed5-ec37b1e47838" />


**Question 5**

Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id | cust_name | city | grade | salesman_id

-------------+----------------+------------+-------+-------------
```
    3002 | Nick Rimando   | New York   |   100 |        5001

    3007 | Brad Davis     | New York   |   200 |        5001

    3005 | Graham Zusi    | California |   200 |        5002
```
```
select COUNT(*) AS COUNT
FROM customer
WHERE grade IS NOT NULL;
```

**Output:**

<img width="637" height="440" alt="image" src="https://github.com/user-attachments/assets/c1f0992a-9177-4c98-b08a-8b5e6c091723" />


**Question 6**

Write a SQL query to find the average length of names for people living in Chennai?

Table: customer

name type

id INTEGER name TEXT
city TEXT email TEXT phone INTEGER

```
select AVG(LENGTH(name)) AS avg_name_length
FROM customer
where city = 'Chennai';
```
**Output:**
<img width="610" height="445" alt="image" src="https://github.com/user-attachments/assets/d3b21055-29d1-4713-a2b0-1247bda8c591" />


**Question 7**

Write a SQL query to find the minimum purchase amount.

Sample table: orders

ord_no purch_amt ord_date customer_id salesman_id

70001 150.5 2012-10-05 3005 5002

70009 270.65 2012-09-10 3001 5005

70002 65.26 2012-10-05 3002 5001

```
select MIN(purch_amt) AS MINIMUM
FROM orders;
```
**Output:**

<img width="545" height="502" alt="image" src="https://github.com/user-attachments/assets/b79116e8-4cac-46a3-b65c-ae69f42c8ce9" />

**Question 8**

Write an SQL query that groups the customer data into 5-year age intervals, calculates the minimum salary for each group, and excludes groups where the minimum salary is not less than 2000.

Table: customer1

```
select 
    (age/5)*5 AS age_group,
    MIN(salary) 
from customer1
group by (age/5)*5
HAVING MIN(salary) < 2000;
```

**Output:**

<img width="837" height="471" alt="image" src="https://github.com/user-attachments/assets/3a5eb8a7-cc9f-4448-80fa-f1845308342e" />

**Question 9**

Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.

Sample table: customer1

```
SELECT (age/5)*5 as age_group,SUM(salary)
from customer1
group by age_group   
having SUM(salary) > 5000;
```
**Output:**

<img width="767" height="480" alt="image" src="https://github.com/user-attachments/assets/8eaa107a-4a6f-4d9b-902e-57e0157c7d90" />

**Question 10**

Write the SQL query that accomplishes the grouping of data by addresses, calculates the sum of salaries for each address, and excludes addresses where the total salary sum is not greater than 2000.

Sample table: customer1

```
SELECT address,SUM(salary)
from customer1
group by address   
having SUM(salary) > 2000;
```

**Output:**

<img width="795" height="612" alt="image" src="https://github.com/user-attachments/assets/7c5cd964-f1d1-4783-b0c1-fba1902d0473" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
