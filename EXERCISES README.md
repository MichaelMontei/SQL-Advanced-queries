# SQL-Advanced-queries-Exercises

-- 1) How many customers do we have?
SELECT * From customers;

-- 2) What is the customer number of Mary Young?
SELECT customerNumber
FROM customers
WHERE contactFirstName = 'Mary'
AND contactLastName = 'Young';

-- 3) What is the customer number of the person living at Magazinweg 7, Frankfurt 60528?
SELECT customerNumber
FROM customers
WHERE addressLine1 = 'Magazinweg 7'
AND city = 'Frankfurt'
AND postalCode = '60528';

-- 4) If you sort the employees on their last name, what is the email of the first employee?
SELECT email
FROM employees
ORDER BY lastName ASC;

-- 5) If you sort the employees on their last name, what is the email of the last employee?
SELECT email
FROM employees
ORDER BY lastName DESC;

-- 6) What is first the product code of all the products from the line 'Trucks and Buses', sorted first by productscale, then by productname.
SELECT productCode, productName
FROM products
WHERE productLine = 'Trucks and Buses'
ORDER BY productScale, productName;

-- 7) What is the email of the first employee, sorted on their last name that starts with a 't'?
SELECT email
FROM employees
WHERE lastName LIKE 't%'
ORDER BY lastName;

-- 8) Which customer (give customer number) payed by check on 2004-01-19?
SELECT customerNumber
FROM payments
WHERE paymentDate = '2004-01-19';

-- 9) How many customers do we have living in the state Nevada or New York?
SELECT state, customerName
FROM customers
WHERE state = 'NEV' OR state = 'NY';

-- 10) How many customers do we have living in the state Nevada or New York or outside the united states?
SELECT count(customerName)
FROM customers
WHERE (state = 'NEV' OR state = 'NY')
OR country != 'USA';

-- 11 How many customers do we have with the following conditions (only 1 query needed):  - Living in the state Nevada or New York OR - Living outside the USA and with a credit limit above 1000 dollar?
SELECT state, creditLimit, count(customerName)
FROM customers
WHERE (state = 'NEV' OR state = 'NY' OR country != 'USA') AND creditLimit > 1000;