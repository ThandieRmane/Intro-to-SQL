# Case Study 1
## Chinook Database

[Chinook Schema link](https://ucde-rey.s3.amazonaws.com/DSV1015/ChinookDatabaseSchema.png)

![Chinook Schema](https://ucde-rey.s3.amazonaws.com/DSV1015/ChinookDatabaseSchema.png)

## Part one: Basic SQL Syntax

#### 1. Retrieve all the records from the Employees table.

``` SQL
Select *
FROM employees;
```
| EmployeeId | LastName | FirstName | Title               | ReportsTo | BirthDate           | HireDate            | Address                     | City       | State | Country | PostalCode | Phone             | Fax               | Email                    |
|------------|----------|-----------|---------------------|-----------|---------------------|---------------------|-----------------------------|------------|-------|---------|------------|-------------------|-------------------|--------------------------|
| 1          | Adams    | Andrew    | General Manager     | None      | 1962-02-18 00:00:00 | 2002-08-14 00:00:00 | 11120 Jasper Ave NW         | Edmonton   | AB    | Canada  | T5K 2N1    | +1 (780) 428-9482 | +1 (780) 428-3457 | andrew@chinookcorp.com   |
| 2          | Edwards  | Nancy     | Sales Manager       | 1         | 1958-12-08 00:00:00 | 2002-05-01 00:00:00 | 825 8 Ave SW                | Calgary    | AB    | Canada  | T2P 2T3    | +1 (403) 262-3443 | +1 (403) 262-3322 | nancy@chinookcorp.com    |
| 3          | Peacock  | Jane      | Sales Support Agent | 2         | 1973-08-29 00:00:00 | 2002-04-01 00:00:00 | 1111 6 Ave SW               | Calgary    | AB    | Canada  | T2P 5M5    | +1 (403) 262-3443 | +1 (403) 262-6712 | jane@chinookcorp.com     |
| 4          | Park     | Margaret  | Sales Support Agent | 2         | 1947-09-19 00:00:00 | 2003-05-03 00:00:00 | 683 10 Street SW            | Calgary    | AB    | Canada  | T2P 5G3    | +1 (403) 263-4423 | +1 (403) 263-4289 | margaret@chinookcorp.com |
| 5          | Johnson  | Steve     | Sales Support Agent | 2         | 1965-03-03 00:00:00 | 2003-10-17 00:00:00 | 7727B 41 Ave                | Calgary    | AB    | Canada  | T3B 1Y7    | 1 (780) 836-9987  | 1 (780) 836-9543  | steve@chinookcorp.com    |

#### 2. Retrieve the FirstName, LastName, Birthdate, Address, City, and State from the Employees table.

``` SQL
SELECT Firstname, Lastname, Birthdate, Address, City, State
FROM Employees;
```

#### 3. Retrieve all the columns from the Tracks table, but only return 20 rows.

``` SQL
SELECT *
FROM tracks
LIMIT 20;
```

## Part 2: Filtering, Sorting and Calculating Data with SQL

#### 1. Find all the tracks that have a length of 5,000,000 milliseconds or more.

``` SQL
select trackid,milliseconds
from tracks
where milliseconds >= '5000000';
```

#### 2. Find all the invoices whose total is between $5 and $15 dollars.

``` SQL
select invoiceid, total
from invoices
where total between '5' and '15';
```

#### 3. Find all the customers from the following States: RJ, DF, AB, BC, CA, WA, NY.

``` SQL
select customerid, state, firstname,lastname,company
from customers
where state in ('RJ','DF','AB','BC','CA','WA','NY');
```

#### 4. Find all the invoices for customer 56 and 58 where the total was between $1.00 and $5.00.

``` SQL
select total, customerid, invoiceid, invoicedate
from invoices
where customerid in ('56','58')and (total between 1 and 5);
```

#### 5. Find all the tracks whose name starts with 'All'.

``` SQL
select Name, trackid
from tracks
where name like 'all%';
```

#### 6. Find all the customer emails that start with "J" and are from gmail.com.

``` SQL
select *
from customers
where email like 'j%@gmail.com';
```

#### 7. Find all the invoices from the billing city Brasília, Edmonton, and Vancouver and sort in descending order by invoice ID.

``` SQL
select *
from invoices
where billingcity in ('Brasilia', 'Edmonton', 'Vancouver')
ORDER BY invoiceid desc;
```

#### 8. Show the number of orders placed by each customer (hint: this is found in the invoices table) and sort the result by the number of orders in descending order.

``` SQL
select *,
count (customerid) as totalorders
from invoices
GROUP BY customerid;
```

#### 9. Find the albums with 12 or more tracks.

``` SQL
Select *, COUNT (trackid) as totaltracks
from tracks 
group by albumid
having count (trackid) >= 12;
```

## Part 3: Subqueries and Joins with SQL

#### 1. Using a subquery, find the names of all the tracks for the album "Californication".

``` SQL
select tracks.name, albums.title
from tracks
join albums on albums.albumid = tracks.albumid
where albums.title in (select title from albums where title like '%cali%');
```

#### 2. Find the total number of invoices for each customer along with the customer's full name, city and email.

``` SQL
SELECT
    COUNT(invoices.invoiceid) AS invoice_count,
    (customers.firstname || ' ' || customers.lastname) AS fullname,
    customers.city,
    customers.email
FROM
    customers
JOIN
    invoices ON customers.customerid = invoices.customerid
GROUP BY
    customers.customerid, fullname, customers.city, customers.email;
```

#### 3. Retrieve the track name, album, artistID, and trackID for all the albums.

``` SQL
select tracks.name, albums.title, albums.artistid, tracks.trackid
from tracks
join albums on albums.albumid = albums.albumid
group by tracks.trackid, tracks.name;
```

#### 4. Retrieve a list with the managers last name, and the last name of the employees who report to him or her.

``` SQL
SELECT
    e1.LastName AS EmployeeLastName,
    e2.LastName AS ManagerLastName
FROM
    employees e1
LEFT JOIN
    employees e2 ON e1.ReportsTo = e2.EmployeeId;
```

#### 5. Find the name and ID of the artists who do not have albums.

``` SQL
SELECT
    artists.ArtistId,
    artists.Name
FROM
    artists
LEFT JOIN
    albums ON artists.ArtistId = albums.ArtistId
WHERE
    albums.AlbumId IS NULL;
```

#### 6. Use a UNION to create a list of all the employee's and customer's first names and last names ordered by the last name in descending order.

``` SQL
Select customers.firstname, customers. lastname
from customers
union 
select employees.firstname, employees.lastname
from employees
order by lastname desc;
```

#### 7. See if there are any customers who have a different city listed in their billing city versus their customer city.

``` SQL
select invoices.customerid, invoices.billingaddress, invoices.billingcity, customers.city
from invoices
join customers on customers.customerid = invoices.customerid;
```

## Part 4: Modyfying and Analyzing Data with SQL

#### 1. Pull a list of customer ids with the customer’s full name, and address, along with combining their city and country together. Be sure to make a space in between these two and make it UPPER CASE. (e.g. LOS ANGELES USA)

``` SQL
select 
customerid,
(firstname || ' ' || lastname) as FullName,
UPPER(city || ' ' || country) as Location

from customers;
```

#### 2. Create a new employee user id by combining the first 4 letters of the employee’s first name with the first 2 letters of the employee’s last name. Make the new field lower case and pull each individual step to show your work.

```SQL
select employeeid, (firstname || ' ' || lastname) as fullname,
lower(substr(firstname, 1,4) || substr(lastname,1,2)) as userid
from employees;
```

#### 3. Show a list of employees who have worked for the company for 15 or more years using the current date function. Sort by lastname ascending.

```SQL
SELECT
    employeeid,
    firstname,
    lastname,
    (julianday(date('now')) - julianday(hiredate)) / 365.25 AS years_diff
FROM
    employees
where years_diff >= 15
ORDER BY
    lastname;
```

#### 4. Profiling the Customers table, answer the following question. Are there any columns with null values?

``` SQL
select * from customers
where postalcode is null;
```

#### 5. Which of the following cities indicate having 2 customers?

``` SQL
select city, count(city) as no_of_cust
from customers
group by city 
order by no_of_cust desc;
```

#### 6. Create a new customer invoice id by combining a customer’s invoice id with their first and last name while ordering your query in the following order: firstname, lastname, and invoiceID.

``` SQL
SELECT
    invoices.invoiceid,
    customers.customerid,
    (customers.firstname || customers.lastname || invoices.invoiceid) AS newcustinvoiceid
FROM
    customers
JOIN
    invoices ON invoices.customerid = customers.customerid
order by newcustinvoiceid;
```
