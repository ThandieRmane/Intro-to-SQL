# Case Study 1
## Chinook Database

[Chinook Schema link](https://ucde-rey.s3.amazonaws.com/DSV1015/ChinookDatabaseSchema.png)

![Chinook Schema](https://ucde-rey.s3.amazonaws.com/DSV1015/ChinookDatabaseSchema.png)

## Part one: Basic SQL Syntax

#### Retrieve all the records from the Employees table.

`Select *
FROM employees;`

#### Retrieve the FirstName, LastName, Birthdate, Address, City, and State from the Employees table.

`SELECT Firstname, Lastname, Birthdate, Address, City, State
FROM Employees`

#### Retrieve all the columns from the Tracks table, but only return 20 rows.

`SELECT *
FROM tracks
LIMIT 20`

## Part 2

#### Find all the tracks that have a length of 5,000,000 milliseconds or more.

#### Find all the invoices whose total is between $5 and $15 dollars.

#### Find all the customers from the following States: RJ, DF, AB, BC, CA, WA, NY.

#### Find all the invoices for customer 56 and 58 where the total was between $1.00 and $5.00.

#### Find all the tracks whose name starts with 'All'.

#### Find all the customer emails that start with "J" and are from gmail.com.

#### Find all the invoices from the billing city Brasília, Edmonton, and Vancouver and sort in descending order by invoice ID.

#### Show the number of orders placed by each customer (hint: this is found in the invoices table) and sort the result by the number of orders in descending order.

#### Find the albums with 12 or more tracks.

## Part 3

#### Using a subquery, find the names of all the tracks for the album "Californication".

#### Find the total number of invoices for each customer along with the customer's full name, city and email.

#### Retrieve the track name, album, artistID, and trackID for all the albums.

#### Retrieve a list with the managers last name, and the last name of the employees who report to him or her.

#### Find the name and ID of the artists who do not have albums.

#### Use a UNION to create a list of all the employee's and customer's first names and last names ordered by the last name in descending order.

#### See if there are any customers who have a different city listed in their billing city versus their customer city.

## Part 4

#### Pull a list of customer ids with the customer’s full name, and address, along with combining their city and country together. Be sure to make a space in between these two and make it UPPER CASE. (e.g. LOS ANGELES USA)

#### Create a new employee user id by combining the first 4 letters of the employee’s first name with the first 2 letters of the employee’s last name. Make the new field lower case and pull each individual step to show your work.

#### Show a list of employees who have worked for the company for 15 or more years using the current date function. Sort by lastname ascending.

#### Profiling the Customers table, answer the following question. Are there any columns with null values?

#### Which of the following cities indicate having 2 customers?

#### Create a new customer invoice id by combining a customer’s invoice id with their first and last name while ordering your query in the following order: firstname, lastname, and invoiceID.
