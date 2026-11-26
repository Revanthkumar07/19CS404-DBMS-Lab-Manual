# Experiment 4: Aggregate Functions, Group By and Having Clause
## NAME: BEEDA VENKATA REVANTH KUMAR
## REG NO: 212224240023

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
```
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?

Sample tablePrescriptions Table



For example:

Result
Frequency      TotalPrescriptions
-------------  ------------------
Every 3 weeks  1
Every 6 hours  1
Once           1
Once daily     4
Once daily at  1
Pending        1
Twice daily    1

```

```sql
select frequency, count(prescriptionid) as TotalPrescriptions from prescriptions group by frequency;
```

**Output:**

<img width="917" height="608" alt="image" src="https://github.com/user-attachments/assets/bc038cc6-0dd0-4f99-b877-357af563e98d" />


**Question 2**
```
How many medical records are there for each patient?

Sample table:MedicalRecords Table



For example:

Result
PatientID   TotalRecords
----------  ------------
4           4
5           1
6           1
7           1
8           1
10          2

```

```sql
select PatientID,count(RecordID) as TotalRecords from MedicalRecords
group by PatientID
```

**Output:**

<img width="736" height="720" alt="image" src="https://github.com/user-attachments/assets/cf384786-2d6a-4a5b-9811-af039441fc1b" />


**Question 3**
```
What is the count of male and female patients?

Sample table: Patients Table



For example:

Result
Gender      TotalPatients
----------  -------------
Female      5
Male        5

```

```sql
SELECT Gender, count(*) as
TotalPatients
from Patients
group by Gender;
```

**Output:**

<img width="722" height="437" alt="image" src="https://github.com/user-attachments/assets/c5f3ffa9-c02c-4611-9fb4-af6fa8b66ad3" />


**Question 4**
```
Write a SQL query to find  how many employees work in California?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
 

For example:

Result
employees_in_california
-----------------------
2

```

```sql
SELECT COUNT(*) AS employees_in_california
FROM employee
WHERE city = 'California';
```

**Output:**

<img width="678" height="381" alt="image" src="https://github.com/user-attachments/assets/7be0e0ee-8c48-4c36-8303-80d88871eaf3" />


**Question 5**
```
Write a SQL query to find the customer with longest name?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
name          length
------------  ----------
Preeti Patel  12

```
```sql
SELECT name, LENGTH(name) AS length
FROM customer
ORDER BY length DESC
LIMIT 1;
```

**Output:**

<img width="708" height="390" alt="image" src="https://github.com/user-attachments/assets/9b08a886-70f0-4297-acc4-8f650d4e11d1" />


**Question 6**
```
Write a SQL query to find the total number of unique cities in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
unique_cities
-------------
10

```

```sql
SELECT COUNT(DISTINCT city) AS unique_cities
FROM customer;
```

**Output:**

<img width="550" height="380" alt="image" src="https://github.com/user-attachments/assets/bc06fdd5-707e-4e20-9e7e-bf4b9dd9047c" />


**Question 7**
```
Write a SQL query to find the maximum purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

 

For example:

Result
MAXIMUM
----------
5760.0

```

```sql
SELECT MAX(purch_amt) as MAXIMUM
FROM orders;
```

**Output:**

<img width="487" height="387" alt="image" src="https://github.com/user-attachments/assets/7217715b-3d8a-4506-b66e-969785baf6d2" />


**Question 8**
```
Write the SQL query that accomplishes the selection of total number of products for each category from the "products" table, and includes only those products where the minimum category ID is less than 3.

Sample table: products



For example:

Result
category_id  count(product_name)
-----------  -------------------
1            4
2            3

```

```sql
SELECT category_id, count(product_name)
FROM products
GROUP BY category_id
HAVING MIN(category_id) < 3;
```

**Output:**

<img width="886" height="442" alt="image" src="https://github.com/user-attachments/assets/185b15ae-cca0-4458-a6dc-cebef7e8c088" />


**Question 9**
```
Write an SQL query that groups the customer data into 5-year age intervals, calculates the minimum salary for each group, and excludes groups where the minimum salary is not less than 2000.

Table: customer1



For example:

Result
age_group   MIN(salary)
----------  -----------
25          1500

```

```sql
SELECT
    (age / 5) * 5 AS age_group,
    MIN(salary)
FROM customer1
GROUP BY age_group
HAVING MIN(salary) < 2000
ORDER BY age_group;
```

**Output:**

<img width="663" height="405" alt="image" src="https://github.com/user-attachments/assets/d097d976-3b9d-4860-892c-cdf51a08d2cb" />


**Question 10**
```
Write the SQL query that accomplishes the grouping of data by addresses, calculates the sum of salaries for each address, and excludes addresses where the total salary sum is not greater than 2000.

Sample table: customer1



For example:

Result
address     SUM(salary)
----------  -----------
Bhopal      8500
Hyderabad   4500
Indore      10000
Mumbai      6500

```

```sql
select address,SUM(salary) from customer1 group by address having SUM(salary)>2000;
```

**Output:**

<img width="740" height="561" alt="image" src="https://github.com/user-attachments/assets/717e57fc-a27c-4783-8589-824aa61660ba" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
