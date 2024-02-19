# Case Study 1
## Chinook Database

[Chinook Schema link](https://ucde-rey.s3.amazonaws.com/DSV1015/ChinookDatabaseSchema.png)

![Chinook Schema](https://ucde-rey.s3.amazonaws.com/DSV1015/ChinookDatabaseSchema.png)

Note: I have limited all results to the first 5 lines 

## Part one: Selecting and retrieving data with SQL

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

| FirstName | LastName | BirthDate           | Address                     | City       | State |
|-----------|----------|---------------------|-----------------------------|------------|-------|
| Andrew    | Adams    | 1962-02-18 00:00:00 | 11120 Jasper Ave NW         | Edmonton   | AB    |
| Nancy     | Edwards  | 1958-12-08 00:00:00 | 825 8 Ave SW                | Calgary    | AB    |
| Jane      | Peacock  | 1973-08-29 00:00:00 | 1111 6 Ave SW               | Calgary    | AB    |
| Margaret  | Park     | 1947-09-19 00:00:00 | 683 10 Street SW            | Calgary    | AB    |
| Steve     | Johnson  | 1965-03-03 00:00:00 | 7727B 41 Ave                | Calgary    | AB    |

#### 3. Retrieve all the columns from the Tracks table, but only return 20 rows.

``` SQL
SELECT *
FROM tracks
LIMIT 20;
```

| TrackId | Name                                    | AlbumId | MediaTypeId | GenreId | Composer                                                               | Milliseconds | Bytes    | UnitPrice |
|---------|-----------------------------------------|---------|-------------|---------|------------------------------------------------------------------------|--------------|----------|-----------|
| 1       | For Those About To Rock (We Salute You) | 1       | 1           | 1       | Angus Young, Malcolm Young, Brian Johnson                              | 343719       | 11170334 | 0.99      |
| 2       | Balls to the Wall                       | 2       | 2           | 1       | None                                                                   | 342562       | 5510424  | 0.99      |
| 3       | Fast As a Shark                         | 3       | 2           | 1       | F. Baltes, S. Kaufman, U. Dirkscneider & W. Hoffman                    | 230619       | 3990994  | 0.99      |
| 4       | Restless and Wild                       | 3       | 2           | 1       | F. Baltes, R.A. Smith-Diesel, S. Kaufman, U. Dirkscneider & W. Hoffman | 252051       | 4331779  | 0.99      |
| 5       | Princess of the Dawn                    | 3       | 2           | 1       | Deaffy & R.A. Smith-Diesel                                             | 375418       | 6290521  | 0.99      |

## Part 2: Filtering, Sorting and Calculating Data with SQL

#### 1. Find all the tracks that have a length of 5,000,000 milliseconds or more.

``` SQL
select trackid,milliseconds
from tracks
where milliseconds >= '5000000';
```

| TrackId | Milliseconds |
|---------|--------------|
| 2820    | 5286953      |
| 3224    | 5088838      |

#### 2. Find all the invoices whose total is between $5 and $15 dollars.

``` SQL
select invoiceid, total
from invoices
where total between '5' and '15';
```

| InvoiceId | Total |
|-----------|-------|
| 3         | 5.94  |
| 4         | 8.91  |
| 5         | 13.86 |
| 10        | 5.94  |
| 11        | 8.91  |
| 12        | 13.86 |
| 17        | 5.94  |
| 18        | 8.91  |
| 19        | 13.86 |
| 24        | 5.94  |

#### 3. Find all the customers from the following States: RJ, DF, AB, BC, CA, WA, NY.

``` SQL
select customerid, state, firstname,lastname,company
from customers
where state in ('RJ','DF','AB','BC','CA','WA','NY');
```

| CustomerId | State | FirstName | LastName | Company               |
|------------|-------|-----------|----------|-----------------------|
| 12         | RJ    | Roberto   | Almeida  | Riotur                |
| 13         | DF    | Fernanda  | Ramos    | None                  |
| 14         | AB    | Mark      | Philips  | Telus                 |
| 15         | BC    | Jennifer  | Peterson | Rogers Canada         |
| 16         | CA    | Frank     | Harris   | Google Inc.           |
| 17         | WA    | Jack      | Smith    | Microsoft Corporation |
| 18         | NY    | Michelle  | Brooks   | None                  |
| 19         | CA    | Tim       | Goyer    | Apple Inc.            |
| 20         | CA    | Dan       | Miller   | None                  |

#### 4. Find all the invoices for customer 56 and 58 where the total was between $1.00 and $5.00.

``` SQL
select total, customerid, invoiceid, invoicedate
from invoices
where customerid in ('56','58')and (total between 1 and 5);
```

| Total | CustomerId | InvoiceId | InvoiceDate         |
|-------|------------|-----------|---------------------|
| 1.98  | 56         | 119       | 2010-06-12 00:00:00 |
| 3.96  | 56         | 142       | 2010-09-14 00:00:00 |
| 1.98  | 56         | 337       | 2013-01-28 00:00:00 |
| 1.98  | 58         | 120       | 2010-06-12 00:00:00 |
| 1.98  | 58         | 315       | 2012-10-27 00:00:00 |
| 3.96  | 58         | 338       | 2013-01-29 00:00:00 |
| 1.99  | 58         | 412       | 2013-12-22 00:00:00 |

#### 5. Find all the tracks whose name starts with 'All'.

``` SQL
select Name, trackid
from tracks
where name like 'all%';
```

| Name                                   | TrackId |
|----------------------------------------|---------|
| All I Really Want                      | 38      |
| All For You                            | 134     |
| All Star                               | 385     |
| All My Life                            | 1009    |
| All My Love                            | 1608    |
| All Within My Hands                    | 1892    |
| All or None                            | 2192    |
| All Dead, All Dead                     | 2274    |
| All the Best Cowboys Have Daddy Issues | 2888    |
| All Because Of You                     | 2969    |
| All Along The Watchtower               | 2991    |
| All I Want Is You                      | 3003    |
| All I Want Is You                      | 3017    |
| All My Love                            | 3316    |
| All Night Thing                        | 3374    |

#### 6. Find all the customer emails that start with "J" and are from gmail.com.

``` SQL
select *
from customers
where email like 'j%@gmail.com';
```

| CustomerId | FirstName | LastName | Company | Address     | City           | State | Country | PostalCode | Phone             | Fax  | Email               | SupportRepId |
|------------|-----------|----------|---------|-------------|----------------|-------|---------|------------|-------------------|------|---------------------|--------------|
| 28         | Julia     | Barnett  | None    | 302 S 700 E | Salt Lake City | UT    | USA     | 84102      | +1 (801) 531-7272 | None | jubarnett@gmail.com | 5            |

#### 7. Find all the invoices from the billing city Brasília, Edmonton, and Vancouver and sort in descending order by invoice ID.

``` SQL
select *
from invoices
where billingcity in ('Brasilia', 'Edmonton', 'Vancouver')
ORDER BY invoiceid desc;
```

| InvoiceId | CustomerId | InvoiceDate         | BillingAddress      | BillingCity | BillingState | BillingCountry | BillingPostalCode | Total |
|-----------|------------|---------------------|---------------------|-------------|--------------|----------------|-------------------|-------|
| 362       | 14         | 2013-05-11 00:00:00 | 8210 111 ST NW      | Edmonton    | AB           | Canada         | T6G 2C7           | 13.86 |
| 351       | 14         | 2013-03-31 00:00:00 | 8210 111 ST NW      | Edmonton    | AB           | Canada         | T6G 2C7           | 1.98  |
| 328       | 15         | 2012-12-15 00:00:00 | 700 W Pender Street | Vancouver   | BC           | Canada         | V6C 1G8           | 0.99  |
| 276       | 15         | 2012-04-26 00:00:00 | 700 W Pender Street | Vancouver   | BC           | Canada         | V6C 1G8           | 5.94  |
| 254       | 15         | 2012-01-23 00:00:00 | 700 W Pender Street | Vancouver   | BC           | Canada         | V6C 1G8           | 3.96  |
| 231       | 15         | 2011-10-21 00:00:00 | 700 W Pender Street | Vancouver   | BC           | Canada         | V6C 1G8           | 1.98  |
| 230       | 14         | 2011-10-08 00:00:00 | 8210 111 ST NW      | Edmonton    | AB           | Canada         | T6G 2C7           | 0.99  |
| 178       | 14         | 2011-02-17 00:00:00 | 8210 111 ST NW      | Edmonton    | AB           | Canada         | T6G 2C7           | 5.94  |
| 156       | 14         | 2010-11-15 00:00:00 | 8210 111 ST NW      | Edmonton    | AB           | Canada         | T6G 2C7           | 3.96  |
| 133       | 14         | 2010-08-13 00:00:00 | 8210 111 ST NW      | Edmonton    | AB           | Canada         | T6G 2C7           | 1.98  |
| 102       | 15         | 2010-03-16 00:00:00 | 700 W Pender Street | Vancouver   | BC           | Canada         | V6C 1G8           | 9.91  |
| 47        | 15         | 2009-07-16 00:00:00 | 700 W Pender Street | Vancouver   | BC           | Canada         | V6C 1G8           | 13.86 |
| 36        | 15         | 2009-06-05 00:00:00 | 700 W Pender Street | Vancouver   | BC           | Canada         | V6C 1G8           | 1.98  |
| 4         | 14         | 2009-01-06 00:00:00 | 8210 111 ST NW      | Edmonton    | AB           | Canada         | T6G 2C7           | 8.91  |

#### 8. Show the number of orders placed by each customer (hint: this is found in the invoices table) and sort the result by the number of orders in descending order.

``` SQL
select *,
count (customerid) as totalorders
from invoices
GROUP BY customerid;
```

| InvoiceId | CustomerId | InvoiceDate         | BillingAddress                       | BillingCity         | BillingState | BillingCountry | BillingPostalCode | Total | totalorders |
|-----------|------------|---------------------|--------------------------------------|---------------------|--------------|----------------|-------------------|-------|-------------|
| 382       | 1          | 2013-08-07 00:00:00 | Av. Brigadeiro Faria Lima, 2170      | São José dos Campos | SP           | Brazil         | 12227-000         | 8.91  | 7           |
| 293       | 2          | 2012-07-13 00:00:00 | Theodor-Heuss-Straße 34              | Stuttgart           | None         | Germany        | 70174             | 0.99  | 7           |
| 391       | 3          | 2013-09-20 00:00:00 | 1498 rue Bélanger                    | Montréal            | QC           | Canada         | H2G 1A7           | 0.99  | 7           |
| 392       | 4          | 2013-10-03 00:00:00 | Ullevålsveien 14                     | Oslo                | None         | Norway         | 0171              | 1.98  | 7           |
| 361       | 5          | 2013-05-06 00:00:00 | Klanova 9/506                        | Prague              | None         | Czech Republic | 14700             | 8.91  | 7           |
| 404       | 6          | 2013-11-13 00:00:00 | Rilská 3174/6                        | Prague              | None         | Czech Republic | 14300             | 25.86 | 7           |
| 370       | 7          | 2013-06-19 00:00:00 | Rotenturmstraße 4, 1010 Innere Stadt | Vienne              | None         | Austria        | 1010              | 0.99  | 7           |
| 394       | 8          | 2013-10-04 00:00:00 | Grétrystraat 63                      | Brussels            | None         | Belgium        | 1000              | 3.96  | 7           |
| 340       | 9          | 2013-02-02 00:00:00 | Sønder Boulevard 51                  | Copenhagen          | None         | Denmark        | 1720              | 8.91  | 7           |
| 383       | 10         | 2013-08-12 00:00:00 | Rua Dr. Falcão Filho, 155            | São Paulo           | SP           | Brazil         | 01007-010         | 13.86 | 7           |

#### 9. Find the albums with 12 or more tracks.

``` SQL
Select *, COUNT (trackid) as totaltracks
from tracks 
group by albumid
having count (trackid) >= 12;
```

| TrackId | Name                         | AlbumId | MediaTypeId | GenreId | Composer                          | Milliseconds |    Bytes | UnitPrice | totaltracks |
|---------|------------------------------|---------|-------------|---------|----------------------------------|--------------|----------|-----------|-------------|
| 37      | Livin' On The Edge           | 5       | 1           | 1       | Steven Tyler, Joe Perry, Mark Hudson | 381231     | 12374569 | 0.99      | 15          |
| 50      | You Oughta Know (Alternate)  | 6       | 1           | 1       | Alanis Morissette & Glenn Ballard | 491885       | 16008629 | 0.99      | 13          |
| 62      | Real Thing                   | 7       | 1           | 1       | Jerry Cantrell, Layne Staley      | 243879       | 7937731  | 0.99      | 12          |
| 76      | Canta, Canta Mais            | 8       | 1           | 2       | None                             | 271856       | 8719426  | 0.99      | 14          |
| 98      | The Last Remaining Light     | 10      | 1           | 1       | Audioslave/Chris Cornell        | 317492       | 7622615  | 0.99      | 14          |

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
