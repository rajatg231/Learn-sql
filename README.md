# **MySQL**
In SQL, there are four main categories of commands: Data Definition Language (*DDL*), Data Manipulation Language (*DML*), Data Control Language (*DCL*), and Transaction Control Language (*TCL*).

## Data Definition Language (DDL):
DDL commands are used to define and manage database objects such as tables, indexes, views, and sequences. DDL commands include:
* CREATE: Used to create new database objects such as tables, views, indexes, and sequences.
* ALTER: Used to modify the structure of an existing database object .
* DROP: Used to delete an existing database object.
* TRUNCATE: Used to remove all data from a table.
* Command examples: CREATE TABLE, CREATE INDEX, 
ALTER TABLE, DROP TABLE, TRUNCATE TABLE

## Data Manipulation Language (DML):
DML commands are used to manipulate data within the database. DML commands include:
* SELECT: Used to retrieve data from one or more tables in a database.
* INSERT: Used to insert new data into a table.
* UPDATE: Used to update existing data within a table.
* DELETE: Used to delete data from a table.
* Command examples:  SELECT, INSERT INTO, UPDATE, DELETE FROM

## Data Control Language (DCL):
DCL commands are used to control access to the database. DCL commands include:
* GRANT: Used to give users permission to perform specific actions on database objects.
* REVOKE: Used to take away permissions that were previously granted to users.
* Command examples: GRANT, REVOKE

## Transaction Control Language (TCL):
TCL commands are used to manage transactions within the database. TCL commands include:
* COMMIT: Used to permanently save changes made in the current transaction.
* ROLLBACK: Used to undo changes made in the current transaction.
* SAVEPOINT: Used to set a point in the transaction where you can later roll back to if needed.
* Command examples: COMMIT, ROLLBACK, SAVEPOINT

> SQL commands to interact with a MySQL database.
## **Login**

```bash
mysql -u root -p
```
The command `mysql -u root -p` is used to open the MySQL command line client as the root user. This command prompts the user to enter the root user's password to authenticate and gain access to the MySQL command line interface.

## **Show Users**

```sql
SELECT User, Host FROM mysql.user;
```
This MySQL command is used to retrieve the list of all users and their corresponding hostnames from the "mysql.user" table.The "mysql.user" table is a system table that stores information about all MySQL users and their privileges.

## **Create User**

```sql
CREATE USER '<username>'@'localhost' IDENTIFIED BY '<password>';
```
This MySQL command is used to create a new user account in the MySQL server. The <username> and <password> values should be replaced with the desired username and password for the new account. The @'localhost' part specifies that this user can only connect to the MySQL server from the same machine (localhost).

## **Grant Privileges On A Databases**

```sql
GRANT SELECT,CREATE,DROP,INSERT,UPDATE,DELETE ON project1.* TO 'user2'@'localhost';
FLUSH PRIVILEGES;
```
This command grants the user named "user2" all permissions (SELECT, CREATE, DROP, INSERT, UPDATE, and DELETE) on the "project1" database, when they access it from the "localhost" server. 
`FLUSH PRIVILEGES;`: This command is used to reload the grant tables in the MySQL server, which updates the privileges for the current user session. It is recommended to run this command after making any changes to the user's privileges.

## **Show Grants**

```sql
SHOW GRANTS FOR 'user2'@'localhost';
```
 This command will display the grants that have been given to the user 'user2' when accessing the database from 'localhost'. This command can be used to verify the privileges of a user and ensure that they have the necessary permissions to perform their intended actions in the database.
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=Black class='medium'>Grants for user2@localhost</td>
</tr>

<tr>
<td class='normal' valign='top'>GRANT USAGE ON *.* TO 'user2'@'localhost'</td>
</tr>

<tr>
<td class='normal' valign='top'>GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP ON 'project1'.* TO 'user2'@'localhost'</td>
</tr>
</table>
</body></html>



## **Remove Grants**

```sql
REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'user2'@'localhost';
```
The above command revokes all privileges and grant option from the user2 account on the localhost in MySQL.
## **Delete User**

```sql
DROP USER 'user2'@'localhost';
```
The above command will delete the user account 'user2'@'localhost' from the MySQL server, including all of its associated privileges and permissions.
## **Exit**

```sql
exit;
```
To exit the mysql terminal.
## **Show Databases**

```sql
SHOW DATABASES;
```
This command is used to display a list of all databases in the MySQL server. It returns a table with a list of database names. This command can be useful to verify that a particular database exists or to choose a database to work with.
## **Create Database**

```sql
CREATE DATABASE project1;
```
This command creates a new database named "project1". 
## **Delete Database**

```sql
DROP DATABASE project1;
```
This SQL command will drop the database named "project1" and permanently delete all tables, data, and other objects contained within it.
## **Select Database**

```sql
USE project1;
```
When we execute the USE statement followed by the name of a database, it makes that database the current working database. All subsequent SQL statements will be executed on this database until a new USE statement is executed to select a different database.

## **Create Table**

```sql
CREATE TABLE USERS (
	id INT,
	first_name VARCHAR(50),
	last_name VARCHAR(50),
	email VARCHAR(50),
	gender VARCHAR(50),
	location VARCHAR(50),
	department VARCHAR(50),
	join_date DATE,
    PRIMARY KEY(id)
);
```
This SQL command creates a new table named "USERS" with columns for "id", "first_name", "last_name", "email", "gender", "location", "department", and "join_date". The "id" column is set as the primary key for the table.

## **Delete / Drop Table**

```sql
DROP TABLE users;
```
This SQL command will drop/delete the table named "users" from the current database.
## **Show Tables**

```sql
SHOW TABLES;
```
This command is used to display a list of all tables in the currently selected database.
#### *Output* 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>Tables_in_project1</td>
</tr>

<tr>
<td class='normal' valign='top'>users</td>
</tr>
</table>
</body></html>

## **Insert Row / Record**
Artificial data was generated for demonstration purposes using [mockaroo.com](https://www.mockaroo.com/).

```sql
INSERT INTO USERS (id, first_name, last_name, email, gender, location, department, join_date) VALUES (1, 'Dolph', 'Buxcy', 'dbuxcy0@usda.gov', 'Male', 'Ecuador', 'Research and Development', '2022-07-22');
```
The command inserts a new row into the USERS table with the specified values for each column.

## **Insert Multiple Rows**
```sql
INSERT INTO USERS (id, first_name, last_name, email, gender, location, department, join_date) VALUES (2, 'Verney', 'Doman', 'vdoman1@statcounter.com', 'Male', 'Ecuador', 'Product Management', '2023-02-22'),
(3, 'Alister', 'Drayton', 'adrayton2@livejournal.com', 'Male', 'Ecuador', 'Legal', '2022-06-12'),
(4, 'Reinhold', 'Killbey', 'rkillbey3@webmd.com', 'Male', 'Ecuador', 'Sales', '2022-07-23'),
(5, 'Hector', 'Splain', 'hsplain4@printfriendly.com', 'Male', 'Ecuador', 'Legal', '2022-02-28'),
(6, 'Rriocard', 'Concannon', 'rconcannon5@boston.com', 'Male', 'Ecuador', 'Research and Development', '2022-10-19'),
(7, 'Wainwright', 'Cinnamond', 'wcinnamond6@mac.com', 'Male', 'Ecuador', 'Support', '2022-10-09'),
(8, 'Kati', 'Blaze', 'kblaze7@kickstarter.com', 'Female', 'Ecuador', 'Sales', '2022-11-20'),
(9, 'Cyndia', 'Hirtz', 'chirtz8@w3.org', 'Female', 'Ecuador', 'Training', '2023-02-19'),
(10, 'Eliot', 'Flacke', 'eflacke9@japanpost.jp', 'Male', 'Ecuador', 'Product Management', '2022-04-11'),
(11, 'Lenna', 'Rickersey', 'lrickerseya@cyberchimps.com', 'Female', 'Ecuador', 'Human Resources', '2022-02-26'),
(12, 'Barny', 'Tanfield', 'btanfieldb@istockphoto.com', 'Male', 'Ecuador', 'Sales', '2022-04-18'),
(13, 'Paolina', 'Quibell', 'pquibellc@odnoklassniki.ru', 'Genderfluid', 'Ecuador', 'Marketing', '2022-11-01'),
(14, 'Marsh', 'Shailer', 'mshailerd@google.cn', 'Male', 'Ecuador', 'Support', '2022-06-06'),
(15, 'Robinett', 'Lyford', 'rlyforde@ucla.edu', 'Female', 'Ecuador', 'Support', '2022-12-03'),
(16, 'Paula', 'Cornelius', 'pcorneliusf@godaddy.com', 'Female', 'Ecuador', 'Training', '2022-07-02'),
(17, 'Paolina', 'Machin', 'pmaching@wunderground.com', 'Female', 'Ecuador', 'Accounting', '2022-12-04'),
(18, 'Caterina', 'Suscens', 'csuscensh@telegraph.co.uk', 'Female', 'Ecuador', 'Marketing', '2022-08-06'),
(19, 'Colline', 'Dalwood', 'cdalwoodi@oakley.com', 'Female', 'Ecuador', 'Services', '2022-07-04'),
(20, 'Dorie', 'Sember', 'dsemberj@springer.com', 'Female', 'Ecuador', 'Business Development', '2022-11-12');
```
The command inserts multiple rows into the USERS table with the specified values for each column.
## **Select**

```sql
SELECT * FROM users;
```
This SQL command selects all columns and rows from the "users" table in the current database.
#### *Output* 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>id</td>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>email</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>location</td>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>join_date</td>
</tr>

<tr>
<td class='normal' valign='top'>1</td>
<td class='normal' valign='top'>Dolph</td>
<td class='normal' valign='top'>Buxcy</td>
<td class='normal' valign='top'>dbuxcy0@usda.gov</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2022-07-22</td>
</tr>

<tr>
<td class='normal' valign='top'>2</td>
<td class='normal' valign='top'>Verney</td>
<td class='normal' valign='top'>Doman</td>
<td class='normal' valign='top'>vdoman1@statcounter.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2023-02-22</td>
</tr>

<tr>
<td class='normal' valign='top'>3</td>
<td class='normal' valign='top'>Alister</td>
<td class='normal' valign='top'>Drayton</td>
<td class='normal' valign='top'>adrayton2@livejournal.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-06-12</td>
</tr>

<tr>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Reinhold</td>
<td class='normal' valign='top'>Killbey</td>
<td class='normal' valign='top'>rkillbey3@webmd.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-07-23</td>
</tr>

<tr>
<td class='normal' valign='top'>5</td>
<td class='normal' valign='top'>Hector</td>
<td class='normal' valign='top'>Splain</td>
<td class='normal' valign='top'>hsplain4@printfriendly.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-02-28</td>
</tr>

<tr>
<td class='normal' valign='top'>6</td>
<td class='normal' valign='top'>Rriocard</td>
<td class='normal' valign='top'>Concannon</td>
<td class='normal' valign='top'>rconcannon5@boston.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2022-10-19</td>
</tr>

<tr>
<td class='normal' valign='top'>7</td>
<td class='normal' valign='top'>Wainwright</td>
<td class='normal' valign='top'>Cinnamond</td>
<td class='normal' valign='top'>wcinnamond6@mac.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-10-09</td>
</tr>

<tr>
<td class='normal' valign='top'>8</td>
<td class='normal' valign='top'>Kati</td>
<td class='normal' valign='top'>Blaze</td>
<td class='normal' valign='top'>kblaze7@kickstarter.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-11-20</td>
</tr>

<tr>
<td class='normal' valign='top'>9</td>
<td class='normal' valign='top'>Cyndia</td>
<td class='normal' valign='top'>Hirtz</td>
<td class='normal' valign='top'>chirtz8@w3.org</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2023-02-19</td>
</tr>

<tr>
<td class='normal' valign='top'>10</td>
<td class='normal' valign='top'>Eliot</td>
<td class='normal' valign='top'>Flacke</td>
<td class='normal' valign='top'>eflacke9@japanpost.jp</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2022-04-11</td>
</tr>

<tr>
<td class='normal' valign='top'>11</td>
<td class='normal' valign='top'>Lenna</td>
<td class='normal' valign='top'>Rickersey</td>
<td class='normal' valign='top'>lrickerseya@cyberchimps.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Human Resources</td>
<td class='normal' valign='top'>2022-02-26</td>
</tr>

<tr>
<td class='normal' valign='top'>12</td>
<td class='normal' valign='top'>Barny</td>
<td class='normal' valign='top'>Tanfield</td>
<td class='normal' valign='top'>btanfieldb@istockphoto.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-04-18</td>
</tr>

<tr>
<td class='normal' valign='top'>13</td>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Quibell</td>
<td class='normal' valign='top'>pquibellc@odnoklassniki.ru</td>
<td class='normal' valign='top'>Genderfluid</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Marketing</td>
<td class='normal' valign='top'>2022-11-01</td>
</tr>

<tr>
<td class='normal' valign='top'>14</td>
<td class='normal' valign='top'>Marsh</td>
<td class='normal' valign='top'>Shailer</td>
<td class='normal' valign='top'>mshailerd@google.cn</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-06-06</td>
</tr>

<tr>
<td class='normal' valign='top'>15</td>
<td class='normal' valign='top'>Robinett</td>
<td class='normal' valign='top'>Lyford</td>
<td class='normal' valign='top'>rlyforde@ucla.edu</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-12-03</td>
</tr>

<tr>
<td class='normal' valign='top'>16</td>
<td class='normal' valign='top'>Paula</td>
<td class='normal' valign='top'>Cornelius</td>
<td class='normal' valign='top'>pcorneliusf@godaddy.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2022-07-02</td>
</tr>

<tr>
<td class='normal' valign='top'>17</td>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Machin</td>
<td class='normal' valign='top'>pmaching@wunderground.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Accounting</td>
<td class='normal' valign='top'>2022-12-04</td>
</tr>

<tr>
<td class='normal' valign='top'>18</td>
<td class='normal' valign='top'>Caterina</td>
<td class='normal' valign='top'>Suscens</td>
<td class='normal' valign='top'>csuscensh@telegraph.co.uk</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Marketing</td>
<td class='normal' valign='top'>2022-08-06</td>
</tr>

<tr>
<td class='normal' valign='top'>19</td>
<td class='normal' valign='top'>Colline</td>
<td class='normal' valign='top'>Dalwood</td>
<td class='normal' valign='top'>cdalwoodi@oakley.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Services</td>
<td class='normal' valign='top'>2022-07-04</td>
</tr>

<tr>
<td class='normal' valign='top'>20</td>
<td class='normal' valign='top'>Dorie</td>
<td class='normal' valign='top'>Sember</td>
<td class='normal' valign='top'>dsemberj@springer.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Business Development</td>
<td class='normal' valign='top'>2022-11-12</td>
</tr>
</table>
</body></html>

```sql
SELECT first_name, last_name FROM users;
```
This SQL command selects all the rows from the users table, but only with the first_name and last_name columns.
#### *Output* 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
</tr>

<tr>
<td class='normal' valign='top'>Dolph</td>
<td class='normal' valign='top'>Buxcy</td>
</tr>

<tr>
<td class='normal' valign='top'>Verney</td>
<td class='normal' valign='top'>Doman</td>
</tr>

<tr>
<td class='normal' valign='top'>Alister</td>
<td class='normal' valign='top'>Drayton</td>
</tr>

<tr>
<td class='normal' valign='top'>Reinhold</td>
<td class='normal' valign='top'>Killbey</td>
</tr>

<tr>
<td class='normal' valign='top'>Hector</td>
<td class='normal' valign='top'>Splain</td>
</tr>

<tr>
<td class='normal' valign='top'>Rriocard</td>
<td class='normal' valign='top'>Concannon</td>
</tr>

<tr>
<td class='normal' valign='top'>Wainwright</td>
<td class='normal' valign='top'>Cinnamond</td>
</tr>

<tr>
<td class='normal' valign='top'>Kati</td>
<td class='normal' valign='top'>Blaze</td>
</tr>

<tr>
<td class='normal' valign='top'>Cyndia</td>
<td class='normal' valign='top'>Hirtz</td>
</tr>

<tr>
<td class='normal' valign='top'>Eliot</td>
<td class='normal' valign='top'>Flacke</td>
</tr>

<tr>
<td class='normal' valign='top'>Lenna</td>
<td class='normal' valign='top'>Rickersey</td>
</tr>

<tr>
<td class='normal' valign='top'>Barny</td>
<td class='normal' valign='top'>Tanfield</td>
</tr>

<tr>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Quibell</td>
</tr>

<tr>
<td class='normal' valign='top'>Marsh</td>
<td class='normal' valign='top'>Shailer</td>
</tr>

<tr>
<td class='normal' valign='top'>Robinett</td>
<td class='normal' valign='top'>Lyford</td>
</tr>

<tr>
<td class='normal' valign='top'>Paula</td>
<td class='normal' valign='top'>Cornelius</td>
</tr>

<tr>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Machin</td>
</tr>

<tr>
<td class='normal' valign='top'>Caterina</td>
<td class='normal' valign='top'>Suscens</td>
</tr>

<tr>
<td class='normal' valign='top'>Colline</td>
<td class='normal' valign='top'>Dalwood</td>
</tr>

<tr>
<td class='normal' valign='top'>Dorie</td>
<td class='normal' valign='top'>Sember</td>
</tr>
</table>
</body></html>

## **Where Clause**
```sql
SELECT * FROM users WHERE gender='Male';
```
This SQL command retrieves all the rows from the users table where the **gender** column has a **value** of '**Male**'.
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>id</td>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>email</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>location</td>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>join_date</td>
</tr>

<tr>
<td class='normal' valign='top'>1</td>
<td class='normal' valign='top'>Dolph</td>
<td class='normal' valign='top'>Buxcy</td>
<td class='normal' valign='top'>dbuxcy0@usda.gov</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2022-07-22</td>
</tr>

<tr>
<td class='normal' valign='top'>2</td>
<td class='normal' valign='top'>Verney</td>
<td class='normal' valign='top'>Doman</td>
<td class='normal' valign='top'>vdoman1@statcounter.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2023-02-22</td>
</tr>

<tr>
<td class='normal' valign='top'>3</td>
<td class='normal' valign='top'>Alister</td>
<td class='normal' valign='top'>Drayton</td>
<td class='normal' valign='top'>adrayton2@livejournal.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-06-12</td>
</tr>

<tr>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Reinhold</td>
<td class='normal' valign='top'>Killbey</td>
<td class='normal' valign='top'>rkillbey3@webmd.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-07-23</td>
</tr>

<tr>
<td class='normal' valign='top'>5</td>
<td class='normal' valign='top'>Hector</td>
<td class='normal' valign='top'>Splain</td>
<td class='normal' valign='top'>hsplain4@printfriendly.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-02-28</td>
</tr>

<tr>
<td class='normal' valign='top'>6</td>
<td class='normal' valign='top'>Rriocard</td>
<td class='normal' valign='top'>Concannon</td>
<td class='normal' valign='top'>rconcannon5@boston.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2022-10-19</td>
</tr>

<tr>
<td class='normal' valign='top'>7</td>
<td class='normal' valign='top'>Wainwright</td>
<td class='normal' valign='top'>Cinnamond</td>
<td class='normal' valign='top'>wcinnamond6@mac.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-10-09</td>
</tr>

<tr>
<td class='normal' valign='top'>10</td>
<td class='normal' valign='top'>Eliot</td>
<td class='normal' valign='top'>Flacke</td>
<td class='normal' valign='top'>eflacke9@japanpost.jp</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2022-04-11</td>
</tr>

<tr>
<td class='normal' valign='top'>12</td>
<td class='normal' valign='top'>Barny</td>
<td class='normal' valign='top'>Tanfield</td>
<td class='normal' valign='top'>btanfieldb@istockphoto.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-04-18</td>
</tr>

<tr>
<td class='normal' valign='top'>14</td>
<td class='normal' valign='top'>Marsh</td>
<td class='normal' valign='top'>Shailer</td>
<td class='normal' valign='top'>mshailerd@google.cn</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-06-06</td>
</tr>
</table>
</body></html>


```sql
SELECT * FROM users WHERE gender='Female' AND department='Training';
```
This SQL command selects all columns from the users table where the **gender** column is equal to "**Female**" and the **department** column is equal to "**Training**".
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>id</td>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>email</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>location</td>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>join_date</td>
</tr>

<tr>
<td class='normal' valign='top'>9</td>
<td class='normal' valign='top'>Cyndia</td>
<td class='normal' valign='top'>Hirtz</td>
<td class='normal' valign='top'>chirtz8@w3.org</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2023-02-19</td>
</tr>

<tr>
<td class='normal' valign='top'>16</td>
<td class='normal' valign='top'>Paula</td>
<td class='normal' valign='top'>Cornelius</td>
<td class='normal' valign='top'>pcorneliusf@godaddy.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2022-07-02</td>
</tr>
</table>
</body></html>


```sql
SELECT * FROM users WHERE gender='Male' AND join_date < '2023-01-01';
```
This SQL command selects all rows from the users table where the **gender** column is '**Male**' and the **join_date** column is **less than January 1st, 2023**.
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>id</td>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>email</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>location</td>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>join_date</td>
</tr>

<tr>
<td class='normal' valign='top'>1</td>
<td class='normal' valign='top'>Dolph</td>
<td class='normal' valign='top'>Buxcy</td>
<td class='normal' valign='top'>dbuxcy0@usda.gov</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2022-07-22</td>
</tr>

<tr>
<td class='normal' valign='top'>3</td>
<td class='normal' valign='top'>Alister</td>
<td class='normal' valign='top'>Drayton</td>
<td class='normal' valign='top'>adrayton2@livejournal.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-06-12</td>
</tr>

<tr>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Reinhold</td>
<td class='normal' valign='top'>Killbey</td>
<td class='normal' valign='top'>rkillbey3@webmd.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-07-23</td>
</tr>

<tr>
<td class='normal' valign='top'>5</td>
<td class='normal' valign='top'>Hector</td>
<td class='normal' valign='top'>Splain</td>
<td class='normal' valign='top'>hsplain4@printfriendly.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-02-28</td>
</tr>

<tr>
<td class='normal' valign='top'>6</td>
<td class='normal' valign='top'>Rriocard</td>
<td class='normal' valign='top'>Concannon</td>
<td class='normal' valign='top'>rconcannon5@boston.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2022-10-19</td>
</tr>

<tr>
<td class='normal' valign='top'>7</td>
<td class='normal' valign='top'>Wainwright</td>
<td class='normal' valign='top'>Cinnamond</td>
<td class='normal' valign='top'>wcinnamond6@mac.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-10-09</td>
</tr>

<tr>
<td class='normal' valign='top'>10</td>
<td class='normal' valign='top'>Eliot</td>
<td class='normal' valign='top'>Flacke</td>
<td class='normal' valign='top'>eflacke9@japanpost.jp</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2022-04-11</td>
</tr>

<tr>
<td class='normal' valign='top'>12</td>
<td class='normal' valign='top'>Barny</td>
<td class='normal' valign='top'>Tanfield</td>
<td class='normal' valign='top'>btanfieldb@istockphoto.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-04-18</td>
</tr>

<tr>
<td class='normal' valign='top'>14</td>
<td class='normal' valign='top'>Marsh</td>
<td class='normal' valign='top'>Shailer</td>
<td class='normal' valign='top'>mshailerd@google.cn</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-06-06</td>
</tr>
</table>
</body></html>


```sql
SELECT * FROM users WHERE gender='Female' and join_date > '2022-01-01';
```
This SQL command selects all columns from the users table where the **gender** column is '**Female**' and the **join_date** column is **after '2022-01-01'**.
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>id</td>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>email</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>location</td>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>join_date</td>
</tr>

<tr>
<td class='normal' valign='top'>8</td>
<td class='normal' valign='top'>Kati</td>
<td class='normal' valign='top'>Blaze</td>
<td class='normal' valign='top'>kblaze7@kickstarter.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-11-20</td>
</tr>

<tr>
<td class='normal' valign='top'>9</td>
<td class='normal' valign='top'>Cyndia</td>
<td class='normal' valign='top'>Hirtz</td>
<td class='normal' valign='top'>chirtz8@w3.org</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2023-02-19</td>
</tr>

<tr>
<td class='normal' valign='top'>11</td>
<td class='normal' valign='top'>Lenna</td>
<td class='normal' valign='top'>Rickersey</td>
<td class='normal' valign='top'>lrickerseya@cyberchimps.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Human Resources</td>
<td class='normal' valign='top'>2022-02-26</td>
</tr>

<tr>
<td class='normal' valign='top'>15</td>
<td class='normal' valign='top'>Robinett</td>
<td class='normal' valign='top'>Lyford</td>
<td class='normal' valign='top'>rlyforde@ucla.edu</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-12-03</td>
</tr>

<tr>
<td class='normal' valign='top'>16</td>
<td class='normal' valign='top'>Paula</td>
<td class='normal' valign='top'>Cornelius</td>
<td class='normal' valign='top'>pcorneliusf@godaddy.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2022-07-02</td>
</tr>

<tr>
<td class='normal' valign='top'>17</td>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Machin</td>
<td class='normal' valign='top'>pmaching@wunderground.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Accounting</td>
<td class='normal' valign='top'>2022-12-04</td>
</tr>

<tr>
<td class='normal' valign='top'>18</td>
<td class='normal' valign='top'>Caterina</td>
<td class='normal' valign='top'>Suscens</td>
<td class='normal' valign='top'>csuscensh@telegraph.co.uk</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Marketing</td>
<td class='normal' valign='top'>2022-08-06</td>
</tr>

<tr>
<td class='normal' valign='top'>19</td>
<td class='normal' valign='top'>Colline</td>
<td class='normal' valign='top'>Dalwood</td>
<td class='normal' valign='top'>cdalwoodi@oakley.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Services</td>
<td class='normal' valign='top'>2022-07-04</td>
</tr>

<tr>
<td class='normal' valign='top'>20</td>
<td class='normal' valign='top'>Dorie</td>
<td class='normal' valign='top'>Sember</td>
<td class='normal' valign='top'>dsemberj@springer.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Business Development</td>
<td class='normal' valign='top'>2022-11-12</td>
</tr>
</table>
</body></html>

## **Delete Row**
```sql
DELETE FROM users WHERE id = 20;
```
This SQL command will delete a row from the users table where the value in the **id** column is equal to **20**.

## Update Row

```sql
UPDATE users SET email = 'dbuxcy01@usda.com' WHERE id = 1;
```
This SQL command **updates** the **email** field of the user with **id 1** in the USERS table to 'dbuxcy01@usda.com'.

## **Add New Column**
```sql
ALTER TABLE users ADD age VARCHAR(3);
```
This SQL command adds a new column called '**age**' to the 'users' table. The column is of **type** **VARCHAR**(3), which means it can store a string of up to 3 characters. The new column will initially have NULL values for all existing rows in the table.

## **Modify Column**
```sql
ALTER TABLE users MODIFY COLUMN age INT(3);
```
This will change the data type of the "age" column to INTEGER and set the maximum length to 3 digits.

## **Delete Column**
```sql
ALTER TABLE users DROP COLUMN age ;
```
The ALTER TABLE statement is used to **modify** the structure of a table, and the **DROP** COLUMN clause is used to **remove a column** from the table. Once the column is dropped, all data in that column will also be deleted.

## **Order By (Sort)**
```sql
SELECT * FROM users ORDER BY first_name ASC;
```
This SQL command selects all the columns from the users table and **sorts** the results in **ascending** order based on the values in the **first_name** column.
#### *Output* 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>id</td>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>email</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>location</td>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>join_date</td>
</tr>

<tr>
<td class='normal' valign='top'>3</td>
<td class='normal' valign='top'>Alister</td>
<td class='normal' valign='top'>Drayton</td>
<td class='normal' valign='top'>adrayton2@livejournal.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-06-12</td>
</tr>

<tr>
<td class='normal' valign='top'>12</td>
<td class='normal' valign='top'>Barny</td>
<td class='normal' valign='top'>Tanfield</td>
<td class='normal' valign='top'>btanfieldb@istockphoto.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-04-18</td>
</tr>

<tr>
<td class='normal' valign='top'>18</td>
<td class='normal' valign='top'>Caterina</td>
<td class='normal' valign='top'>Suscens</td>
<td class='normal' valign='top'>csuscensh@telegraph.co.uk</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Marketing</td>
<td class='normal' valign='top'>2022-08-06</td>
</tr>

<tr>
<td class='normal' valign='top'>19</td>
<td class='normal' valign='top'>Colline</td>
<td class='normal' valign='top'>Dalwood</td>
<td class='normal' valign='top'>cdalwoodi@oakley.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Services</td>
<td class='normal' valign='top'>2022-07-04</td>
</tr>

<tr>
<td class='normal' valign='top'>9</td>
<td class='normal' valign='top'>Cyndia</td>
<td class='normal' valign='top'>Hirtz</td>
<td class='normal' valign='top'>chirtz8@w3.org</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2023-02-19</td>
</tr>

<tr>
<td class='normal' valign='top'>1</td>
<td class='normal' valign='top'>Dolph</td>
<td class='normal' valign='top'>Buxcy</td>
<td class='normal' valign='top'>dbuxcy01@usda.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2022-07-22</td>
</tr>

<tr>
<td class='normal' valign='top'>10</td>
<td class='normal' valign='top'>Eliot</td>
<td class='normal' valign='top'>Flacke</td>
<td class='normal' valign='top'>eflacke9@japanpost.jp</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2022-04-11</td>
</tr>

<tr>
<td class='normal' valign='top'>5</td>
<td class='normal' valign='top'>Hector</td>
<td class='normal' valign='top'>Splain</td>
<td class='normal' valign='top'>hsplain4@printfriendly.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-02-28</td>
</tr>

<tr>
<td class='normal' valign='top'>8</td>
<td class='normal' valign='top'>Kati</td>
<td class='normal' valign='top'>Blaze</td>
<td class='normal' valign='top'>kblaze7@kickstarter.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-11-20</td>
</tr>

<tr>
<td class='normal' valign='top'>11</td>
<td class='normal' valign='top'>Lenna</td>
<td class='normal' valign='top'>Rickersey</td>
<td class='normal' valign='top'>lrickerseya@cyberchimps.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Human Resources</td>
<td class='normal' valign='top'>2022-02-26</td>
</tr>

<tr>
<td class='normal' valign='top'>14</td>
<td class='normal' valign='top'>Marsh</td>
<td class='normal' valign='top'>Shailer</td>
<td class='normal' valign='top'>mshailerd@google.cn</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-06-06</td>
</tr>

<tr>
<td class='normal' valign='top'>13</td>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Quibell</td>
<td class='normal' valign='top'>pquibellc@odnoklassniki.ru</td>
<td class='normal' valign='top'>Genderfluid</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Marketing</td>
<td class='normal' valign='top'>2022-11-01</td>
</tr>

<tr>
<td class='normal' valign='top'>17</td>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Machin</td>
<td class='normal' valign='top'>pmaching@wunderground.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Accounting</td>
<td class='normal' valign='top'>2022-12-04</td>
</tr>

<tr>
<td class='normal' valign='top'>16</td>
<td class='normal' valign='top'>Paula</td>
<td class='normal' valign='top'>Cornelius</td>
<td class='normal' valign='top'>pcorneliusf@godaddy.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2022-07-02</td>
</tr>

<tr>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Reinhold</td>
<td class='normal' valign='top'>Killbey</td>
<td class='normal' valign='top'>rkillbey3@webmd.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-07-23</td>
</tr>

<tr>
<td class='normal' valign='top'>15</td>
<td class='normal' valign='top'>Robinett</td>
<td class='normal' valign='top'>Lyford</td>
<td class='normal' valign='top'>rlyforde@ucla.edu</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-12-03</td>
</tr>

<tr>
<td class='normal' valign='top'>6</td>
<td class='normal' valign='top'>Rriocard</td>
<td class='normal' valign='top'>Concannon</td>
<td class='normal' valign='top'>rconcannon5@boston.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2022-10-19</td>
</tr>

<tr>
<td class='normal' valign='top'>2</td>
<td class='normal' valign='top'>Verney</td>
<td class='normal' valign='top'>Doman</td>
<td class='normal' valign='top'>vdoman1@statcounter.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2023-02-22</td>
</tr>

<tr>
<td class='normal' valign='top'>7</td>
<td class='normal' valign='top'>Wainwright</td>
<td class='normal' valign='top'>Cinnamond</td>
<td class='normal' valign='top'>wcinnamond6@mac.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-10-09</td>
</tr>
</table>
</body></html>


```sql
SELECT * FROM users ORDER BY join_date DESC;
```
This SQL command selects all the rows from the "users" table and **orders** them by the "**join_date**" column in **descending** order. The most recently joined users will appear first in the result set.
#### *Output* 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>id</td>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>email</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>location</td>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>join_date</td>
</tr>

<tr>
<td class='normal' valign='top'>2</td>
<td class='normal' valign='top'>Verney</td>
<td class='normal' valign='top'>Doman</td>
<td class='normal' valign='top'>vdoman1@statcounter.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2023-02-22</td>
</tr>

<tr>
<td class='normal' valign='top'>9</td>
<td class='normal' valign='top'>Cyndia</td>
<td class='normal' valign='top'>Hirtz</td>
<td class='normal' valign='top'>chirtz8@w3.org</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2023-02-19</td>
</tr>

<tr>
<td class='normal' valign='top'>17</td>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Machin</td>
<td class='normal' valign='top'>pmaching@wunderground.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Accounting</td>
<td class='normal' valign='top'>2022-12-04</td>
</tr>

<tr>
<td class='normal' valign='top'>15</td>
<td class='normal' valign='top'>Robinett</td>
<td class='normal' valign='top'>Lyford</td>
<td class='normal' valign='top'>rlyforde@ucla.edu</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-12-03</td>
</tr>

<tr>
<td class='normal' valign='top'>8</td>
<td class='normal' valign='top'>Kati</td>
<td class='normal' valign='top'>Blaze</td>
<td class='normal' valign='top'>kblaze7@kickstarter.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-11-20</td>
</tr>

<tr>
<td class='normal' valign='top'>13</td>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Quibell</td>
<td class='normal' valign='top'>pquibellc@odnoklassniki.ru</td>
<td class='normal' valign='top'>Genderfluid</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Marketing</td>
<td class='normal' valign='top'>2022-11-01</td>
</tr>

<tr>
<td class='normal' valign='top'>6</td>
<td class='normal' valign='top'>Rriocard</td>
<td class='normal' valign='top'>Concannon</td>
<td class='normal' valign='top'>rconcannon5@boston.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2022-10-19</td>
</tr>

<tr>
<td class='normal' valign='top'>7</td>
<td class='normal' valign='top'>Wainwright</td>
<td class='normal' valign='top'>Cinnamond</td>
<td class='normal' valign='top'>wcinnamond6@mac.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-10-09</td>
</tr>

<tr>
<td class='normal' valign='top'>18</td>
<td class='normal' valign='top'>Caterina</td>
<td class='normal' valign='top'>Suscens</td>
<td class='normal' valign='top'>csuscensh@telegraph.co.uk</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Marketing</td>
<td class='normal' valign='top'>2022-08-06</td>
</tr>

<tr>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Reinhold</td>
<td class='normal' valign='top'>Killbey</td>
<td class='normal' valign='top'>rkillbey3@webmd.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-07-23</td>
</tr>

<tr>
<td class='normal' valign='top'>1</td>
<td class='normal' valign='top'>Dolph</td>
<td class='normal' valign='top'>Buxcy</td>
<td class='normal' valign='top'>dbuxcy01@usda.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2022-07-22</td>
</tr>

<tr>
<td class='normal' valign='top'>19</td>
<td class='normal' valign='top'>Colline</td>
<td class='normal' valign='top'>Dalwood</td>
<td class='normal' valign='top'>cdalwoodi@oakley.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Services</td>
<td class='normal' valign='top'>2022-07-04</td>
</tr>

<tr>
<td class='normal' valign='top'>16</td>
<td class='normal' valign='top'>Paula</td>
<td class='normal' valign='top'>Cornelius</td>
<td class='normal' valign='top'>pcorneliusf@godaddy.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2022-07-02</td>
</tr>

<tr>
<td class='normal' valign='top'>3</td>
<td class='normal' valign='top'>Alister</td>
<td class='normal' valign='top'>Drayton</td>
<td class='normal' valign='top'>adrayton2@livejournal.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-06-12</td>
</tr>

<tr>
<td class='normal' valign='top'>14</td>
<td class='normal' valign='top'>Marsh</td>
<td class='normal' valign='top'>Shailer</td>
<td class='normal' valign='top'>mshailerd@google.cn</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-06-06</td>
</tr>

<tr>
<td class='normal' valign='top'>12</td>
<td class='normal' valign='top'>Barny</td>
<td class='normal' valign='top'>Tanfield</td>
<td class='normal' valign='top'>btanfieldb@istockphoto.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-04-18</td>
</tr>

<tr>
<td class='normal' valign='top'>10</td>
<td class='normal' valign='top'>Eliot</td>
<td class='normal' valign='top'>Flacke</td>
<td class='normal' valign='top'>eflacke9@japanpost.jp</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2022-04-11</td>
</tr>

<tr>
<td class='normal' valign='top'>5</td>
<td class='normal' valign='top'>Hector</td>
<td class='normal' valign='top'>Splain</td>
<td class='normal' valign='top'>hsplain4@printfriendly.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-02-28</td>
</tr>

<tr>
<td class='normal' valign='top'>11</td>
<td class='normal' valign='top'>Lenna</td>
<td class='normal' valign='top'>Rickersey</td>
<td class='normal' valign='top'>lrickerseya@cyberchimps.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Ecuador</td>
<td class='normal' valign='top'>Human Resources</td>
<td class='normal' valign='top'>2022-02-26</td>
</tr>
</table>
</body></html>

## **Concatenate Columns**
```sql
SELECT CONCAT(first_name, ' ', last_name) AS 'Name', department FROM users;
```
This SQL statement selects the **first name, last name**, and **concatenates** them into a **single** column with the alias '**Name**', as well as the department from the 'users' table.
#### *Output* 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>Name</td>
<td bgcolor=black class='medium'>department</td>
</tr>

<tr>
<td class='normal' valign='top'>Dolph Buxcy</td>
<td class='normal' valign='top'>Research and Development</td>
</tr>

<tr>
<td class='normal' valign='top'>Verney Doman</td>
<td class='normal' valign='top'>Product Management</td>
</tr>

<tr>
<td class='normal' valign='top'>Alister Drayton</td>
<td class='normal' valign='top'>Legal</td>
</tr>

<tr>
<td class='normal' valign='top'>Reinhold Killbey</td>
<td class='normal' valign='top'>Sales</td>
</tr>

<tr>
<td class='normal' valign='top'>Hector Splain</td>
<td class='normal' valign='top'>Legal</td>
</tr>

<tr>
<td class='normal' valign='top'>Rriocard Concannon</td>
<td class='normal' valign='top'>Research and Development</td>
</tr>

<tr>
<td class='normal' valign='top'>Wainwright Cinnamond</td>
<td class='normal' valign='top'>Support</td>
</tr>

<tr>
<td class='normal' valign='top'>Kati Blaze</td>
<td class='normal' valign='top'>Sales</td>
</tr>

<tr>
<td class='normal' valign='top'>Cyndia Hirtz</td>
<td class='normal' valign='top'>Training</td>
</tr>

<tr>
<td class='normal' valign='top'>Eliot Flacke</td>
<td class='normal' valign='top'>Product Management</td>
</tr>

<tr>
<td class='normal' valign='top'>Lenna Rickersey</td>
<td class='normal' valign='top'>Human Resources</td>
</tr>

<tr>
<td class='normal' valign='top'>Barny Tanfield</td>
<td class='normal' valign='top'>Sales</td>
</tr>

<tr>
<td class='normal' valign='top'>Paolina Quibell</td>
<td class='normal' valign='top'>Marketing</td>
</tr>

<tr>
<td class='normal' valign='top'>Marsh Shailer</td>
<td class='normal' valign='top'>Support</td>
</tr>

<tr>
<td class='normal' valign='top'>Robinett Lyford</td>
<td class='normal' valign='top'>Support</td>
</tr>

<tr>
<td class='normal' valign='top'>Paula Cornelius</td>
<td class='normal' valign='top'>Training</td>
</tr>

<tr>
<td class='normal' valign='top'>Paolina Machin</td>
<td class='normal' valign='top'>Accounting</td>
</tr>

<tr>
<td class='normal' valign='top'>Caterina Suscens</td>
<td class='normal' valign='top'>Marketing</td>
</tr>

<tr>
<td class='normal' valign='top'>Colline Dalwood</td>
<td class='normal' valign='top'>Services</td>
</tr>
</table>
</body></html>

## **Update Column Values**
```sql
UPDATE USERS SET location = 'China' WHERE id=1;
UPDATE USERS SET location = 'China' WHERE id=2;
UPDATE USERS SET location = 'Thailand' WHERE id=3;
UPDATE USERS SET location = 'Thailand' WHERE id=4;
UPDATE USERS SET location = 'Russia' WHERE id=5;
UPDATE USERS SET location = 'Indonesia' WHERE id=6;
UPDATE USERS SET location = 'China' WHERE id=7;
UPDATE USERS SET location = 'Indonesia' WHERE id=8;
UPDATE USERS SET location = 'Philippines' WHERE id=9;
UPDATE USERS SET location = 'China' WHERE id=10;
UPDATE USERS SET location = 'China' WHERE id=11;
UPDATE USERS SET location = 'Indonesia' WHERE id=12;
UPDATE USERS SET location = 'Argentina' WHERE id=13;
UPDATE USERS SET location = 'China' WHERE id=14;
UPDATE USERS SET location = 'Vanuatu' WHERE id=15;
UPDATE USERS SET location = 'Guatemala' WHERE id=16;
UPDATE USERS SET location = 'Philippines' WHERE id=17;
UPDATE USERS SET location = 'Japan' WHERE id=18;
UPDATE USERS SET location = 'Russia' WHERE id=19;
```
This command will update the values of location in the users table.

## **Select Distinct Rows**
```sql
SELECT DISTINCT location FROM users;
```
This SQL query selects all the **distinct** (unique) values of the "**location**" column from the "users" table.
#### *Output* 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>location</td>
</tr>

<tr>
<td class='normal' valign='top'>China</td>
</tr>

<tr>
<td class='normal' valign='top'>Thailand</td>
</tr>

<tr>
<td class='normal' valign='top'>Russia</td>
</tr>

<tr>
<td class='normal' valign='top'>Indonesia</td>
</tr>

<tr>
<td class='normal' valign='top'>Philippines</td>
</tr>

<tr>
<td class='normal' valign='top'>Argentina</td>
</tr>

<tr>
<td class='normal' valign='top'>Vanuatu</td>
</tr>

<tr>
<td class='normal' valign='top'>Guatemala</td>
</tr>

<tr>
<td class='normal' valign='top'>Japan</td>
</tr>
</table>
</body></html>


## **Between (Select Range)**

```sql
SELECT * FROM users WHERE join_date BETWEEN '2022-06-01' AND '2022-08-01';
```
This SQL query retrieves all the rows from the users table where the **join_date** falls **between** June 1, 2022, and August 1, 2022, **inclusive**.
#### *Output* 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>id</td>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>email</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>location</td>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>join_date</td>
</tr>

<tr>
<td class='normal' valign='top'>1</td>
<td class='normal' valign='top'>Dolph</td>
<td class='normal' valign='top'>Buxcy</td>
<td class='normal' valign='top'>dbuxcy01@usda.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>China</td>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2022-07-22</td>
</tr>

<tr>
<td class='normal' valign='top'>3</td>
<td class='normal' valign='top'>Alister</td>
<td class='normal' valign='top'>Drayton</td>
<td class='normal' valign='top'>adrayton2@livejournal.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Thailand</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-06-12</td>
</tr>

<tr>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Reinhold</td>
<td class='normal' valign='top'>Killbey</td>
<td class='normal' valign='top'>rkillbey3@webmd.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Thailand</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-07-23</td>
</tr>

<tr>
<td class='normal' valign='top'>14</td>
<td class='normal' valign='top'>Marsh</td>
<td class='normal' valign='top'>Shailer</td>
<td class='normal' valign='top'>mshailerd@google.cn</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>China</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-06-06</td>
</tr>

<tr>
<td class='normal' valign='top'>16</td>
<td class='normal' valign='top'>Paula</td>
<td class='normal' valign='top'>Cornelius</td>
<td class='normal' valign='top'>pcorneliusf@godaddy.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Guatemala</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2022-07-02</td>
</tr>

<tr>
<td class='normal' valign='top'>19</td>
<td class='normal' valign='top'>Colline</td>
<td class='normal' valign='top'>Dalwood</td>
<td class='normal' valign='top'>cdalwoodi@oakley.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Russia</td>
<td class='normal' valign='top'>Services</td>
<td class='normal' valign='top'>2022-07-04</td>
</tr>
</table>
</body></html>

## **Like (Searching)**
```sql
SELECT * FROM users WHERE first_name LIKE 'R%';
```
This SQL command selects all columns and rows from the users table where the **first_name** column **starts** with the letter **'R'**. The **%** character is a wildcard that can match **any sequence** of characters, so the LIKE operator 'R%' matches any string that starts with **'R', followed by zero or more** characters.
#### *Output* 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>id</td>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>email</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>location</td>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>join_date</td>
</tr>

<tr>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Reinhold</td>
<td class='normal' valign='top'>Killbey</td>
<td class='normal' valign='top'>rkillbey3@webmd.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Thailand</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-07-23</td>
</tr>

<tr>
<td class='normal' valign='top'>6</td>
<td class='normal' valign='top'>Rriocard</td>
<td class='normal' valign='top'>Concannon</td>
<td class='normal' valign='top'>rconcannon5@boston.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Indonesia</td>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2022-10-19</td>
</tr>

<tr>
<td class='normal' valign='top'>15</td>
<td class='normal' valign='top'>Robinett</td>
<td class='normal' valign='top'>Lyford</td>
<td class='normal' valign='top'>rlyforde@ucla.edu</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Vanuatu</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-12-03</td>
</tr>
</table>
</body></html>


```sql
SELECT * FROM users WHERE first_name LIKE 'Pa%';
```
This query will select all the rows from the "users" table where the "**first_name**" column **starts** with the letters "**Pa**".
#### *Output* 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>id</td>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>email</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>location</td>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>join_date</td>
</tr>

<tr>
<td class='normal' valign='top'>13</td>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Quibell</td>
<td class='normal' valign='top'>pquibellc@odnoklassniki.ru</td>
<td class='normal' valign='top'>Genderfluid</td>
<td class='normal' valign='top'>Argentina</td>
<td class='normal' valign='top'>Marketing</td>
<td class='normal' valign='top'>2022-11-01</td>
</tr>

<tr>
<td class='normal' valign='top'>16</td>
<td class='normal' valign='top'>Paula</td>
<td class='normal' valign='top'>Cornelius</td>
<td class='normal' valign='top'>pcorneliusf@godaddy.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Guatemala</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2022-07-02</td>
</tr>

<tr>
<td class='normal' valign='top'>17</td>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Machin</td>
<td class='normal' valign='top'>pmaching@wunderground.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Philippines</td>
<td class='normal' valign='top'>Accounting</td>
<td class='normal' valign='top'>2022-12-04</td>
</tr>
</table>
</body></html>


```sql
SELECT * FROM users WHERE last_name LIKE '%n';
```
This query will select all the records from the users table where the **last_name** column **ends** with the letter '**n**'.
#### *Output* 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>id</td>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>email</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>location</td>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>join_date</td>
</tr>

<tr>
<td class='normal' valign='top'>2</td>
<td class='normal' valign='top'>Verney</td>
<td class='normal' valign='top'>Doman</td>
<td class='normal' valign='top'>vdoman1@statcounter.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>China</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2023-02-22</td>
</tr>

<tr>
<td class='normal' valign='top'>3</td>
<td class='normal' valign='top'>Alister</td>
<td class='normal' valign='top'>Drayton</td>
<td class='normal' valign='top'>adrayton2@livejournal.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Thailand</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-06-12</td>
</tr>

<tr>
<td class='normal' valign='top'>5</td>
<td class='normal' valign='top'>Hector</td>
<td class='normal' valign='top'>Splain</td>
<td class='normal' valign='top'>hsplain4@printfriendly.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Russia</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-02-28</td>
</tr>

<tr>
<td class='normal' valign='top'>6</td>
<td class='normal' valign='top'>Rriocard</td>
<td class='normal' valign='top'>Concannon</td>
<td class='normal' valign='top'>rconcannon5@boston.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Indonesia</td>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2022-10-19</td>
</tr>

<tr>
<td class='normal' valign='top'>17</td>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Machin</td>
<td class='normal' valign='top'>pmaching@wunderground.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Philippines</td>
<td class='normal' valign='top'>Accounting</td>
<td class='normal' valign='top'>2022-12-04</td>
</tr>
</table>
</body></html>


```sql
SELECT * FROM users WHERE last_name LIKE '%l%';
```
This SQL query will select all the rows from the "users" table where the "**last_name**" column **contains** the letter **"l"** **anywhere** in the string.
#### *Output* 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>id</td>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>email</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>location</td>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>join_date</td>
</tr>

<tr>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Reinhold</td>
<td class='normal' valign='top'>Killbey</td>
<td class='normal' valign='top'>rkillbey3@webmd.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Thailand</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-07-23</td>
</tr>

<tr>
<td class='normal' valign='top'>5</td>
<td class='normal' valign='top'>Hector</td>
<td class='normal' valign='top'>Splain</td>
<td class='normal' valign='top'>hsplain4@printfriendly.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Russia</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-02-28</td>
</tr>

<tr>
<td class='normal' valign='top'>8</td>
<td class='normal' valign='top'>Kati</td>
<td class='normal' valign='top'>Blaze</td>
<td class='normal' valign='top'>kblaze7@kickstarter.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Indonesia</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-11-20</td>
</tr>

<tr>
<td class='normal' valign='top'>10</td>
<td class='normal' valign='top'>Eliot</td>
<td class='normal' valign='top'>Flacke</td>
<td class='normal' valign='top'>eflacke9@japanpost.jp</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>China</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2022-04-11</td>
</tr>

<tr>
<td class='normal' valign='top'>12</td>
<td class='normal' valign='top'>Barny</td>
<td class='normal' valign='top'>Tanfield</td>
<td class='normal' valign='top'>btanfieldb@istockphoto.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Indonesia</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-04-18</td>
</tr>

<tr>
<td class='normal' valign='top'>13</td>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Quibell</td>
<td class='normal' valign='top'>pquibellc@odnoklassniki.ru</td>
<td class='normal' valign='top'>Genderfluid</td>
<td class='normal' valign='top'>Argentina</td>
<td class='normal' valign='top'>Marketing</td>
<td class='normal' valign='top'>2022-11-01</td>
</tr>

<tr>
<td class='normal' valign='top'>14</td>
<td class='normal' valign='top'>Marsh</td>
<td class='normal' valign='top'>Shailer</td>
<td class='normal' valign='top'>mshailerd@google.cn</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>China</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-06-06</td>
</tr>

<tr>
<td class='normal' valign='top'>15</td>
<td class='normal' valign='top'>Robinett</td>
<td class='normal' valign='top'>Lyford</td>
<td class='normal' valign='top'>rlyforde@ucla.edu</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Vanuatu</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-12-03</td>
</tr>

<tr>
<td class='normal' valign='top'>16</td>
<td class='normal' valign='top'>Paula</td>
<td class='normal' valign='top'>Cornelius</td>
<td class='normal' valign='top'>pcorneliusf@godaddy.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Guatemala</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2022-07-02</td>
</tr>

<tr>
<td class='normal' valign='top'>19</td>
<td class='normal' valign='top'>Colline</td>
<td class='normal' valign='top'>Dalwood</td>
<td class='normal' valign='top'>cdalwoodi@oakley.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Russia</td>
<td class='normal' valign='top'>Services</td>
<td class='normal' valign='top'>2022-07-04</td>
</tr>
</table>
</body></html>


## **Not Like**
```sql
SELECT * FROM users WHERE first_name NOT LIKE 'R%';
```
This query will retrieve all the rows from the users table where the **first_name** column **does not start with** the letter **"R"**.
#### *Output* 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>id</td>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>email</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>location</td>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>join_date</td>
</tr>

<tr>
<td class='normal' valign='top'>1</td>
<td class='normal' valign='top'>Dolph</td>
<td class='normal' valign='top'>Buxcy</td>
<td class='normal' valign='top'>dbuxcy01@usda.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>China</td>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2022-07-22</td>
</tr>

<tr>
<td class='normal' valign='top'>2</td>
<td class='normal' valign='top'>Verney</td>
<td class='normal' valign='top'>Doman</td>
<td class='normal' valign='top'>vdoman1@statcounter.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>China</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2023-02-22</td>
</tr>

<tr>
<td class='normal' valign='top'>3</td>
<td class='normal' valign='top'>Alister</td>
<td class='normal' valign='top'>Drayton</td>
<td class='normal' valign='top'>adrayton2@livejournal.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Thailand</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-06-12</td>
</tr>

<tr>
<td class='normal' valign='top'>5</td>
<td class='normal' valign='top'>Hector</td>
<td class='normal' valign='top'>Splain</td>
<td class='normal' valign='top'>hsplain4@printfriendly.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Russia</td>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2022-02-28</td>
</tr>

<tr>
<td class='normal' valign='top'>7</td>
<td class='normal' valign='top'>Wainwright</td>
<td class='normal' valign='top'>Cinnamond</td>
<td class='normal' valign='top'>wcinnamond6@mac.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>China</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-10-09</td>
</tr>

<tr>
<td class='normal' valign='top'>8</td>
<td class='normal' valign='top'>Kati</td>
<td class='normal' valign='top'>Blaze</td>
<td class='normal' valign='top'>kblaze7@kickstarter.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Indonesia</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-11-20</td>
</tr>

<tr>
<td class='normal' valign='top'>9</td>
<td class='normal' valign='top'>Cyndia</td>
<td class='normal' valign='top'>Hirtz</td>
<td class='normal' valign='top'>chirtz8@w3.org</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Philippines</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2023-02-19</td>
</tr>

<tr>
<td class='normal' valign='top'>10</td>
<td class='normal' valign='top'>Eliot</td>
<td class='normal' valign='top'>Flacke</td>
<td class='normal' valign='top'>eflacke9@japanpost.jp</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>China</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2022-04-11</td>
</tr>

<tr>
<td class='normal' valign='top'>11</td>
<td class='normal' valign='top'>Lenna</td>
<td class='normal' valign='top'>Rickersey</td>
<td class='normal' valign='top'>lrickerseya@cyberchimps.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>China</td>
<td class='normal' valign='top'>Human Resources</td>
<td class='normal' valign='top'>2022-02-26</td>
</tr>

<tr>
<td class='normal' valign='top'>12</td>
<td class='normal' valign='top'>Barny</td>
<td class='normal' valign='top'>Tanfield</td>
<td class='normal' valign='top'>btanfieldb@istockphoto.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Indonesia</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-04-18</td>
</tr>

<tr>
<td class='normal' valign='top'>13</td>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Quibell</td>
<td class='normal' valign='top'>pquibellc@odnoklassniki.ru</td>
<td class='normal' valign='top'>Genderfluid</td>
<td class='normal' valign='top'>Argentina</td>
<td class='normal' valign='top'>Marketing</td>
<td class='normal' valign='top'>2022-11-01</td>
</tr>

<tr>
<td class='normal' valign='top'>14</td>
<td class='normal' valign='top'>Marsh</td>
<td class='normal' valign='top'>Shailer</td>
<td class='normal' valign='top'>mshailerd@google.cn</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>China</td>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>2022-06-06</td>
</tr>

<tr>
<td class='normal' valign='top'>16</td>
<td class='normal' valign='top'>Paula</td>
<td class='normal' valign='top'>Cornelius</td>
<td class='normal' valign='top'>pcorneliusf@godaddy.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Guatemala</td>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2022-07-02</td>
</tr>

<tr>
<td class='normal' valign='top'>17</td>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Machin</td>
<td class='normal' valign='top'>pmaching@wunderground.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Philippines</td>
<td class='normal' valign='top'>Accounting</td>
<td class='normal' valign='top'>2022-12-04</td>
</tr>

<tr>
<td class='normal' valign='top'>18</td>
<td class='normal' valign='top'>Caterina</td>
<td class='normal' valign='top'>Suscens</td>
<td class='normal' valign='top'>csuscensh@telegraph.co.uk</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Japan</td>
<td class='normal' valign='top'>Marketing</td>
<td class='normal' valign='top'>2022-08-06</td>
</tr>

<tr>
<td class='normal' valign='top'>19</td>
<td class='normal' valign='top'>Colline</td>
<td class='normal' valign='top'>Dalwood</td>
<td class='normal' valign='top'>cdalwoodi@oakley.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Russia</td>
<td class='normal' valign='top'>Services</td>
<td class='normal' valign='top'>2022-07-04</td>
</tr>
</table>
</body></html>


## **IN**
```sql
SELECT * FROM users WHERE department IN ('Sales', 'Marketing','Product Management');
```
This query will select all the rows from the users table where the value in the **department** column is **either** **'Sales', 'Marketing', or 'Product Management'**.
#### *Output* 
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>id</td>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>email</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>location</td>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>join_date</td>
</tr>

<tr>
<td class='normal' valign='top'>2</td>
<td class='normal' valign='top'>Verney</td>
<td class='normal' valign='top'>Doman</td>
<td class='normal' valign='top'>vdoman1@statcounter.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>China</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2023-02-22</td>
</tr>

<tr>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Reinhold</td>
<td class='normal' valign='top'>Killbey</td>
<td class='normal' valign='top'>rkillbey3@webmd.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Thailand</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-07-23</td>
</tr>

<tr>
<td class='normal' valign='top'>8</td>
<td class='normal' valign='top'>Kati</td>
<td class='normal' valign='top'>Blaze</td>
<td class='normal' valign='top'>kblaze7@kickstarter.com</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Indonesia</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-11-20</td>
</tr>

<tr>
<td class='normal' valign='top'>10</td>
<td class='normal' valign='top'>Eliot</td>
<td class='normal' valign='top'>Flacke</td>
<td class='normal' valign='top'>eflacke9@japanpost.jp</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>China</td>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2022-04-11</td>
</tr>

<tr>
<td class='normal' valign='top'>12</td>
<td class='normal' valign='top'>Barny</td>
<td class='normal' valign='top'>Tanfield</td>
<td class='normal' valign='top'>btanfieldb@istockphoto.com</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Indonesia</td>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>2022-04-18</td>
</tr>

<tr>
<td class='normal' valign='top'>13</td>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Quibell</td>
<td class='normal' valign='top'>pquibellc@odnoklassniki.ru</td>
<td class='normal' valign='top'>Genderfluid</td>
<td class='normal' valign='top'>Argentina</td>
<td class='normal' valign='top'>Marketing</td>
<td class='normal' valign='top'>2022-11-01</td>
</tr>

<tr>
<td class='normal' valign='top'>18</td>
<td class='normal' valign='top'>Caterina</td>
<td class='normal' valign='top'>Suscens</td>
<td class='normal' valign='top'>csuscensh@telegraph.co.uk</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Japan</td>
<td class='normal' valign='top'>Marketing</td>
<td class='normal' valign='top'>2022-08-06</td>
</tr>
</table>
</body></html>

## **Create & Remove Index**
```sql
CREATE INDEX LIndex On users(location);
DROP INDEX LIndex ON users;
```
The first command **creates** an **index** named "**LIndex**" on the "**location**" column of the "users" table. This will **improve the performance of queries** that use the "**location**" column in the **WHERE** clause.
The second command drops the "LIndex" index from the "users" table.

## **New Table With Foreign Key (*Orders*)**

```sql
CREATE TABLE ORDERS (
    id INT PRIMARY KEY,
    user_id INT,
    product_name VARCHAR(50),
    price DECIMAL(10, 2),
    order_date DATE,
    FOREIGN KEY (user_id) REFERENCES USERS(id)
);
```
This command will create a new table called "**ORDERS**" with five columns: **"id"** as **integer** and the **primary key**, "**user_id**" as **integer** and a **foreign key** **referencing** the **"id"** column in the "**USERS**" table, "product_name" as varchar(50), "price" as decimal(10,2), and "order_date" as date.

## **Add Data to *Orders* Table**
```sql
INSERT INTO ORDERS (id, user_id, product_name, price, order_date) VALUES 
(1, 3, 'Laptop', 1200.00, '2022-06-15'),
(2, 5, 'Smartphone', 800.00, '2022-03-02'),
(3, 7, 'Tablet', 500.00, '2022-11-01'),
(4, 9, 'Camera', 900.00, '2023-01-05'),
(5, 11, 'Headphones', 100.00, '2022-03-10'),
(6, 13, 'Smartwatch', 350.00, '2022-12-18'),
(7, 15, 'TV', 1200.00, '2022-12-01'),
(8, 17, 'Monitor', 500.00, '2022-12-04'),
(9, 19, 'Printer', 200.00, '2022-07-20'),
(10, 1, 'Speaker', 80.00, '2022-08-13');
```
This command will insert multiple values in **ORDERS** table.

## **New Table With Foreign Key (*Reviews*)**
```sql
CREATE TABLE reviews (
  id INT PRIMARY KEY,
  user_id INT,
  order_id INT,
  product_name VARCHAR(50),
  rating INT,
  review_text VARCHAR(255),
  FOREIGN KEY (user_id) REFERENCES users(id),
  FOREIGN KEY (order_id) REFERENCES orders(id)
);
```
This SQL command will create a new table named "**reviews**" with columns id, user_id, order_id, product_name, rating, review_text, and **foreign key** constraints on **user_id** and **order_id** **referencing** the **id** column of the **users** and **orders** table respectively. The **id** column is defined as the **primary key** of the table.

## **Add Data to *Orders* Table**
```sql
INSERT INTO Reviews (id, user_id, product_name, rating, review_text, order_id)
VALUES
(1, 2, 'Smartphone', 4, 'Great phone, good battery life.', 2),
(2, 4, 'Laptop', 5, 'Excellent performance, highly recommended.', 1),
(3, 6, 'Smartwatch', 3, 'Average quality, not worth the price.', 6),
(4, 8, 'TV', 5, 'Amazing picture and sound quality.', 7),
(5, 10, 'Headphones', 2, 'Poor sound quality, uncomfortable to wear.', 5),
(6, 12, 'Printer', 4, 'Good value for money, easy to set up.', 9),
(7, 14, 'Monitor', 4, 'Good display, easy to adjust settings.', 8),
(8, 16, 'Camera', 5, 'Excellent image quality, easy to use.', 4),
(9, 18, 'Tablet', 3, 'Average performance, not very durable.', 3);
```
This command will insert multiple values in **REVIEWS** table.

## **INNER JOIN**
```sql
SELECT 
	U.first_name, U.last_name, U.gender, 
	O.product_name, O.price, O.order_date
FROM Users U
INNER JOIN Orders O
ON U.id = O.user_id
ORDER BY O.price;

```
This query will return column first_name, last_name, gender from **Users** table and product_name, price, order_date from **Orders** table where there is a matching user ID.
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>product_name</td>
<td bgcolor=black class='medium'>price</td>
<td bgcolor=black class='medium'>order_date</td>
</tr>

<tr>
<td class='normal' valign='top'>Dolph</td>
<td class='normal' valign='top'>Buxcy</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Speaker</td>
<td class='normal' valign='top'>80.00</td>
<td class='normal' valign='top'>2022-08-13</td>
</tr>

<tr>
<td class='normal' valign='top'>Lenna</td>
<td class='normal' valign='top'>Rickersey</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Headphones</td>
<td class='normal' valign='top'>100.00</td>
<td class='normal' valign='top'>2022-03-10</td>
</tr>

<tr>
<td class='normal' valign='top'>Colline</td>
<td class='normal' valign='top'>Dalwood</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Printer</td>
<td class='normal' valign='top'>200.00</td>
<td class='normal' valign='top'>2022-07-20</td>
</tr>

<tr>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Quibell</td>
<td class='normal' valign='top'>Genderfluid</td>
<td class='normal' valign='top'>Smartwatch</td>
<td class='normal' valign='top'>350.00</td>
<td class='normal' valign='top'>2022-12-18</td>
</tr>

<tr>
<td class='normal' valign='top'>Wainwright</td>
<td class='normal' valign='top'>Cinnamond</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Tablet</td>
<td class='normal' valign='top'>500.00</td>
<td class='normal' valign='top'>2022-11-01</td>
</tr>

<tr>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Machin</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Monitor</td>
<td class='normal' valign='top'>500.00</td>
<td class='normal' valign='top'>2022-12-04</td>
</tr>

<tr>
<td class='normal' valign='top'>Hector</td>
<td class='normal' valign='top'>Splain</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Smartphone</td>
<td class='normal' valign='top'>800.00</td>
<td class='normal' valign='top'>2022-03-02</td>
</tr>

<tr>
<td class='normal' valign='top'>Cyndia</td>
<td class='normal' valign='top'>Hirtz</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Camera</td>
<td class='normal' valign='top'>900.00</td>
<td class='normal' valign='top'>2023-01-05</td>
</tr>

<tr>
<td class='normal' valign='top'>Alister</td>
<td class='normal' valign='top'>Drayton</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Laptop</td>
<td class='normal' valign='top'>1200.00</td>
<td class='normal' valign='top'>2022-06-15</td>
</tr>

<tr>
<td class='normal' valign='top'>Robinett</td>
<td class='normal' valign='top'>Lyford</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>TV</td>
<td class='normal' valign='top'>1200.00</td>
<td class='normal' valign='top'>2022-12-01</td>
</tr>
</table>
</body></html>

## **Left Join**
```sql
SELECT 
	U.first_name, U.last_name, U.gender, 
	O.product_name, O.price, O.order_date
FROM Users U
LEFT JOIN Orders O
ON U.id = O.user_id
ORDER BY O.product_name DESC;
```
This query will return column first_name, last_name, gender from **Users** table and product_name, price, order_date from **Orders** table where there is a matching user ID, plus first_name, last_name, gender from **Users** table for any users that do not have any orders. **If a user does not have any orders**, the **columns** for the "**Orders**" table will have **NULL** values.
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>product_name</td>
<td bgcolor=black class='medium'>price</td>
<td bgcolor=black class='medium'>order_date</td>
</tr>

<tr>
<td class='normal' valign='top'>Robinett</td>
<td class='normal' valign='top'>Lyford</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>TV</td>
<td class='normal' valign='top'>1200.00</td>
<td class='normal' valign='top'>2022-12-01</td>
</tr>

<tr>
<td class='normal' valign='top'>Wainwright</td>
<td class='normal' valign='top'>Cinnamond</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Tablet</td>
<td class='normal' valign='top'>500.00</td>
<td class='normal' valign='top'>2022-11-01</td>
</tr>

<tr>
<td class='normal' valign='top'>Dolph</td>
<td class='normal' valign='top'>Buxcy</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Speaker</td>
<td class='normal' valign='top'>80.00</td>
<td class='normal' valign='top'>2022-08-13</td>
</tr>

<tr>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Quibell</td>
<td class='normal' valign='top'>Genderfluid</td>
<td class='normal' valign='top'>Smartwatch</td>
<td class='normal' valign='top'>350.00</td>
<td class='normal' valign='top'>2022-12-18</td>
</tr>

<tr>
<td class='normal' valign='top'>Hector</td>
<td class='normal' valign='top'>Splain</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Smartphone</td>
<td class='normal' valign='top'>800.00</td>
<td class='normal' valign='top'>2022-03-02</td>
</tr>

<tr>
<td class='normal' valign='top'>Colline</td>
<td class='normal' valign='top'>Dalwood</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Printer</td>
<td class='normal' valign='top'>200.00</td>
<td class='normal' valign='top'>2022-07-20</td>
</tr>

<tr>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Machin</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Monitor</td>
<td class='normal' valign='top'>500.00</td>
<td class='normal' valign='top'>2022-12-04</td>
</tr>

<tr>
<td class='normal' valign='top'>Alister</td>
<td class='normal' valign='top'>Drayton</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Laptop</td>
<td class='normal' valign='top'>1200.00</td>
<td class='normal' valign='top'>2022-06-15</td>
</tr>

<tr>
<td class='normal' valign='top'>Lenna</td>
<td class='normal' valign='top'>Rickersey</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Headphones</td>
<td class='normal' valign='top'>100.00</td>
<td class='normal' valign='top'>2022-03-10</td>
</tr>

<tr>
<td class='normal' valign='top'>Cyndia</td>
<td class='normal' valign='top'>Hirtz</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Camera</td>
<td class='normal' valign='top'>900.00</td>
<td class='normal' valign='top'>2023-01-05</td>
</tr>

<tr>
<td class='normal' valign='top'>Verney</td>
<td class='normal' valign='top'>Doman</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Reinhold</td>
<td class='normal' valign='top'>Killbey</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Rriocard</td>
<td class='normal' valign='top'>Concannon</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Kati</td>
<td class='normal' valign='top'>Blaze</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Eliot</td>
<td class='normal' valign='top'>Flacke</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Barny</td>
<td class='normal' valign='top'>Tanfield</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Marsh</td>
<td class='normal' valign='top'>Shailer</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Paula</td>
<td class='normal' valign='top'>Cornelius</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Caterina</td>
<td class='normal' valign='top'>Suscens</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>
</table>
</body></html>

## **Right Join**
```sql
SELECT 
	U.first_name, U.last_name, U.gender, 
	R.product_name, R.rating, R.review_text
FROM Users U
RIGHT JOIN Reviews R
ON U.id = R.user_id
ORDER BY R.rating DESC;
```
This query will return column first_name, last_name, gender from **Users** table and product_name, rating, review_text from **Reviews** table where there is a matching user ID, plus product_name, rating, review_text from **Reviews** table where there is no corresponding user ID in the "Users" table. **If a review does not have a corresponding user ID**, the **columns** for the "**Users**" table will have **NULL** values.
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>product_name</td>
<td bgcolor=black class='medium'>rating</td>
<td bgcolor=black class='medium'>review_text</td>
</tr>

<tr>
<td class='normal' valign='top'>Reinhold</td>
<td class='normal' valign='top'>Killbey</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Laptop</td>
<td class='normal' valign='top'>5</td>
<td class='normal' valign='top'>Excellent performance, highly recommended.</td>
</tr>

<tr>
<td class='normal' valign='top'>Kati</td>
<td class='normal' valign='top'>Blaze</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>TV</td>
<td class='normal' valign='top'>5</td>
<td class='normal' valign='top'>Amazing picture and sound quality.</td>
</tr>

<tr>
<td class='normal' valign='top'>Paula</td>
<td class='normal' valign='top'>Cornelius</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Camera</td>
<td class='normal' valign='top'>5</td>
<td class='normal' valign='top'>Excellent image quality, easy to use.</td>
</tr>

<tr>
<td class='normal' valign='top'>Verney</td>
<td class='normal' valign='top'>Doman</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Smartphone</td>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Great phone, good battery life.</td>
</tr>

<tr>
<td class='normal' valign='top'>Barny</td>
<td class='normal' valign='top'>Tanfield</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Printer</td>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Good value for money, easy to set up.</td>
</tr>

<tr>
<td class='normal' valign='top'>Marsh</td>
<td class='normal' valign='top'>Shailer</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Monitor</td>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Good display, easy to adjust settings.</td>
</tr>

<tr>
<td class='normal' valign='top'>Rriocard</td>
<td class='normal' valign='top'>Concannon</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Smartwatch</td>
<td class='normal' valign='top'>3</td>
<td class='normal' valign='top'>Average quality, not worth the price.</td>
</tr>

<tr>
<td class='normal' valign='top'>Caterina</td>
<td class='normal' valign='top'>Suscens</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Tablet</td>
<td class='normal' valign='top'>3</td>
<td class='normal' valign='top'>Average performance, not very durable.</td>
</tr>

<tr>
<td class='normal' valign='top'>Eliot</td>
<td class='normal' valign='top'>Flacke</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Headphones</td>
<td class='normal' valign='top'>2</td>
<td class='normal' valign='top'>Poor sound quality, uncomfortable to wear.</td>
</tr>
</table>
</body></html>

## **Full Outer Join**
### Normal syntax
```sql
SELECT U.first_name, U.last_name, U.gender, O.product_name, O.price
FROM Users U
FULL OUTER JOIN Orders O ON U.id = O.user_id
```
This query will return column first_name, last_name, gender from **Users** table and product_name, price from **Orders** table where there is a matching user ID and all above columns for any users that do not have orders and any orders that do not have a corresponding user ID. If there is no corresponding user ID, the columns for the "Users" table will have NULL values and If there is no corresponding order ID, the columns for the "Order" table will have NULL values. Note that FULL OUTER JOINs are not supported in all SQL dialects. So in mysql we will use Left join and right join to achieve full outer join / full join.

```sql
SELECT U.first_name, U.last_name, U.gender, O.product_name, O.price
FROM Users U
LEFT JOIN Orders O ON U.id = O.user_id
UNION
SELECT U.first_name, U.last_name, U.gender, O.product_name, O.price
FROM Users U
RIGHT JOIN Orders O ON U.id = O.user_id;
```
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>product_name</td>
<td bgcolor=black class='medium'>price</td>
</tr>

<tr>
<td class='normal' valign='top'>Dolph</td>
<td class='normal' valign='top'>Buxcy</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Speaker</td>
<td class='normal' valign='top'>80.00</td>
</tr>

<tr>
<td class='normal' valign='top'>Verney</td>
<td class='normal' valign='top'>Doman</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Alister</td>
<td class='normal' valign='top'>Drayton</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Laptop</td>
<td class='normal' valign='top'>1200.00</td>
</tr>

<tr>
<td class='normal' valign='top'>Reinhold</td>
<td class='normal' valign='top'>Killbey</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Hector</td>
<td class='normal' valign='top'>Splain</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Smartphone</td>
<td class='normal' valign='top'>800.00</td>
</tr>

<tr>
<td class='normal' valign='top'>Rriocard</td>
<td class='normal' valign='top'>Concannon</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Wainwright</td>
<td class='normal' valign='top'>Cinnamond</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Tablet</td>
<td class='normal' valign='top'>500.00</td>
</tr>

<tr>
<td class='normal' valign='top'>Kati</td>
<td class='normal' valign='top'>Blaze</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Cyndia</td>
<td class='normal' valign='top'>Hirtz</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Camera</td>
<td class='normal' valign='top'>900.00</td>
</tr>

<tr>
<td class='normal' valign='top'>Eliot</td>
<td class='normal' valign='top'>Flacke</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Lenna</td>
<td class='normal' valign='top'>Rickersey</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Headphones</td>
<td class='normal' valign='top'>100.00</td>
</tr>

<tr>
<td class='normal' valign='top'>Barny</td>
<td class='normal' valign='top'>Tanfield</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Quibell</td>
<td class='normal' valign='top'>Genderfluid</td>
<td class='normal' valign='top'>Smartwatch</td>
<td class='normal' valign='top'>350.00</td>
</tr>

<tr>
<td class='normal' valign='top'>Marsh</td>
<td class='normal' valign='top'>Shailer</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Robinett</td>
<td class='normal' valign='top'>Lyford</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>TV</td>
<td class='normal' valign='top'>1200.00</td>
</tr>

<tr>
<td class='normal' valign='top'>Paula</td>
<td class='normal' valign='top'>Cornelius</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Machin</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Monitor</td>
<td class='normal' valign='top'>500.00</td>
</tr>

<tr>
<td class='normal' valign='top'>Caterina</td>
<td class='normal' valign='top'>Suscens</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Colline</td>
<td class='normal' valign='top'>Dalwood</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Printer</td>
<td class='normal' valign='top'>200.00</td>
</tr>
</table>
</body></html>

## Join Multiple Tables

```sql
SELECT U.first_name, U.last_name, U.gender, O.product_name, O.price, R.rating, R.review_text
FROM Users U
LEFT JOIN Orders O ON U.id = O.user_id
LEFT JOIN Reviews R ON O.id = R.order_id
UNION
SELECT U.first_name, U.last_name, U.gender, O.product_name, O.price, R.rating, R.review_text
FROM Users U
RIGHT JOIN Orders O ON U.id = O.user_id
RIGHT JOIN Reviews R ON O.id = R.order_id;
```
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>first_name</td>
<td bgcolor=black class='medium'>last_name</td>
<td bgcolor=black class='medium'>gender</td>
<td bgcolor=black class='medium'>product_name</td>
<td bgcolor=black class='medium'>price</td>
<td bgcolor=black class='medium'>rating</td>
<td bgcolor=black class='medium'>review_text</td>
</tr>

<tr>
<td class='normal' valign='top'>Dolph</td>
<td class='normal' valign='top'>Buxcy</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Speaker</td>
<td class='normal' valign='top'>80.00</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Verney</td>
<td class='normal' valign='top'>Doman</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Alister</td>
<td class='normal' valign='top'>Drayton</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Laptop</td>
<td class='normal' valign='top'>1200.00</td>
<td class='normal' valign='top'>5</td>
<td class='normal' valign='top'>Excellent performance, highly recommended.</td>
</tr>

<tr>
<td class='normal' valign='top'>Reinhold</td>
<td class='normal' valign='top'>Killbey</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Hector</td>
<td class='normal' valign='top'>Splain</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Smartphone</td>
<td class='normal' valign='top'>800.00</td>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Great phone, good battery life.</td>
</tr>

<tr>
<td class='normal' valign='top'>Rriocard</td>
<td class='normal' valign='top'>Concannon</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Wainwright</td>
<td class='normal' valign='top'>Cinnamond</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>Tablet</td>
<td class='normal' valign='top'>500.00</td>
<td class='normal' valign='top'>3</td>
<td class='normal' valign='top'>Average performance, not very durable.</td>
</tr>

<tr>
<td class='normal' valign='top'>Kati</td>
<td class='normal' valign='top'>Blaze</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Cyndia</td>
<td class='normal' valign='top'>Hirtz</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Camera</td>
<td class='normal' valign='top'>900.00</td>
<td class='normal' valign='top'>5</td>
<td class='normal' valign='top'>Excellent image quality, easy to use.</td>
</tr>

<tr>
<td class='normal' valign='top'>Eliot</td>
<td class='normal' valign='top'>Flacke</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Lenna</td>
<td class='normal' valign='top'>Rickersey</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Headphones</td>
<td class='normal' valign='top'>100.00</td>
<td class='normal' valign='top'>2</td>
<td class='normal' valign='top'>Poor sound quality, uncomfortable to wear.</td>
</tr>

<tr>
<td class='normal' valign='top'>Barny</td>
<td class='normal' valign='top'>Tanfield</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Quibell</td>
<td class='normal' valign='top'>Genderfluid</td>
<td class='normal' valign='top'>Smartwatch</td>
<td class='normal' valign='top'>350.00</td>
<td class='normal' valign='top'>3</td>
<td class='normal' valign='top'>Average quality, not worth the price.</td>
</tr>

<tr>
<td class='normal' valign='top'>Marsh</td>
<td class='normal' valign='top'>Shailer</td>
<td class='normal' valign='top'>Male</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Robinett</td>
<td class='normal' valign='top'>Lyford</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>TV</td>
<td class='normal' valign='top'>1200.00</td>
<td class='normal' valign='top'>5</td>
<td class='normal' valign='top'>Amazing picture and sound quality.</td>
</tr>

<tr>
<td class='normal' valign='top'>Paula</td>
<td class='normal' valign='top'>Cornelius</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Paolina</td>
<td class='normal' valign='top'>Machin</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Monitor</td>
<td class='normal' valign='top'>500.00</td>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Good display, easy to adjust settings.</td>
</tr>

<tr>
<td class='normal' valign='top'>Caterina</td>
<td class='normal' valign='top'>Suscens</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
<td class='normal' valign='top'>NULL</td>
</tr>

<tr>
<td class='normal' valign='top'>Colline</td>
<td class='normal' valign='top'>Dalwood</td>
<td class='normal' valign='top'>Female</td>
<td class='normal' valign='top'>Printer</td>
<td class='normal' valign='top'>200.00</td>
<td class='normal' valign='top'>4</td>
<td class='normal' valign='top'>Good value for money, easy to set up.</td>
</tr>
</table>
</body></html>

## **Aggregate Functions**
```sql
SELECT COUNT(Product_name) FROM orders;
```
This SQL command selects the **count** of the **number of products** in the **orders** table.
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>COUNT(Product_name)</td>
</tr>

<tr>
<td class='normal' valign='top'>10</td>
</tr>
</table>
</body></html>

```sql
SELECT MAX(price) FROM orders;
```
This SQL query will return the **maximum** value of the **price** column from the orders table.
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>MAX(price)</td>
</tr>

<tr>
<td class='normal' valign='top'>1200.00</td>
</tr>
</table>
</body></html>

```sql
SELECT MIN(price) FROM orders;
```
This SQL query will return the **minimum** value of the **price** column from the orders table.
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>MIN(price)</td>
</tr>
<tr>
<td class='normal' valign='top'>80.00</td>
</tr>
</table>
</body></html>

```sql
SELECT SUM(price) FROM orders;
```
This command will return the **sum** of **all** the **values** in the **price** column of the orders table.
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>SUM(price)</td>
</tr>
<tr>
<td class='normal' valign='top'>5830.00</td>
</tr>
</table>
</body></html>

```sql
SELECT UCASE(product_name) ,LCASE(product_name) FROM orders;
```
This query will select two columns, one with the **product_name** in **uppercase** format and the other with the **product_name** in **lowercase** format, from the ORDERS table.
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>UCASE(product_name)</td>
<td bgcolor=black class='medium'>LCASE(product_name)</td>
</tr>

<tr>
<td class='normal' valign='top'>LAPTOP</td>
<td class='normal' valign='top'>laptop</td>
</tr>

<tr>
<td class='normal' valign='top'>SMARTPHONE</td>
<td class='normal' valign='top'>smartphone</td>
</tr>

<tr>
<td class='normal' valign='top'>TABLET</td>
<td class='normal' valign='top'>tablet</td>
</tr>

<tr>
<td class='normal' valign='top'>CAMERA</td>
<td class='normal' valign='top'>camera</td>
</tr>

<tr>
<td class='normal' valign='top'>HEADPHONES</td>
<td class='normal' valign='top'>headphones</td>
</tr>

<tr>
<td class='normal' valign='top'>SMARTWATCH</td>
<td class='normal' valign='top'>smartwatch</td>
</tr>

<tr>
<td class='normal' valign='top'>TV</td>
<td class='normal' valign='top'>tv</td>
</tr>

<tr>
<td class='normal' valign='top'>MONITOR</td>
<td class='normal' valign='top'>monitor</td>
</tr>

<tr>
<td class='normal' valign='top'>PRINTER</td>
<td class='normal' valign='top'>printer</td>
</tr>

<tr>
<td class='normal' valign='top'>SPEAKER</td>
<td class='normal' valign='top'>speaker</td>
</tr>
</table>
</body></html>

## **Group By**

```sql
SELECT department, COUNT(department) FROM users
GROUP BY department;
```
This SQL query is used to **retrieve** the **count of users** in **each department**. The GROUP BY clause is used to **group** the **results** **by the department column**, and the **COUNT**() function is used to **count** the **number of occurrences of each department** in the table. 
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>COUNT(department)</td>
</tr>

<tr>
<td class='normal' valign='top'>Research and Development</td>
<td class='normal' valign='top'>2</td>
</tr>

<tr>
<td class='normal' valign='top'>Product Management</td>
<td class='normal' valign='top'>2</td>
</tr>

<tr>
<td class='normal' valign='top'>Legal</td>
<td class='normal' valign='top'>2</td>
</tr>

<tr>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>3</td>
</tr>

<tr>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>3</td>
</tr>

<tr>
<td class='normal' valign='top'>Training</td>
<td class='normal' valign='top'>2</td>
</tr>

<tr>
<td class='normal' valign='top'>Human Resources</td>
<td class='normal' valign='top'>1</td>
</tr>

<tr>
<td class='normal' valign='top'>Marketing</td>
<td class='normal' valign='top'>2</td>
</tr>

<tr>
<td class='normal' valign='top'>Accounting</td>
<td class='normal' valign='top'>1</td>
</tr>

<tr>
<td class='normal' valign='top'>Services</td>
<td class='normal' valign='top'>1</td>
</tr>
</table>
</body></html>


```sql
SELECT department, COUNT(department) FROM users
WHERE department LIKE 'S%'
GROUP BY department;
```
This SQL query selects the department and the **count of each department** from the users table where the **department** name **starts with the letter 'S'**. The results are grouped by department using the GROUP BY clause.
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>COUNT(department)</td>
</tr>

<tr>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>3</td>
</tr>

<tr>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>3</td>
</tr>

<tr>
<td class='normal' valign='top'>Services</td>
<td class='normal' valign='top'>1</td>
</tr>
</table>
</body></html>


```sql
SELECT department, COUNT(department) FROM users
GROUP BY department
HAVING COUNT(department)>2;
```
This SQL query will **group** the users table **by department** and **count** the **number of users** in each department. Then, it will **filter** the departments where the **count is greater than 2** using the **HAVING** clause. The resulting table will have two columns, department and the count of users in that department, for all departments with more than 2 users.
#### *Output*
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>
<body>
<table border=1>
<tr>
<td bgcolor=black class='medium'>department</td>
<td bgcolor=black class='medium'>COUNT(department)</td>
</tr>

<tr>
<td class='normal' valign='top'>Sales</td>
<td class='normal' valign='top'>3</td>
</tr>

<tr>
<td class='normal' valign='top'>Support</td>
<td class='normal' valign='top'>3</td>
</tr>
</table>
</body></html>

### Credits
* [Traversy media](https://www.youtube.com/channel/UC29ju8bIPH5as8OGnQzwJyA). 
