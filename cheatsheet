1. [Examples](#eg)
1. [Rules for better schema](#schema)
2. [Commands](#commands)
 	1. [SELECT](#select)
		1) [FROM](#from)
		2) [DISTINCT](#dist)
		3) [INTO](#into)
		4) [TOP](#top)
		5) [AS](#as)
		6) [FROM](#from)
	2. [WHERE](#where)
		1) [AND](#and)
		2) [OR](#or)
		3) [BETWEEN](#between)
		4) [LIKE](#like)
		5) [IN](#in)
		6) [IS NULL](#isnull)
		7) [IS NOT NULL](#notnull)
	3. [CREATE](#create)
		1) [DATABASE](#db)
		2) [TABLE](#table)
		3) [INDEX](#index)
		4) [VIEW](#view)
	3. [DROP](#drop)
		1) [DROP DATABASE](#dropdb)
		2) [DROP TABLE](#droptb)
		3) [DROP INDEX](#dropidx)
		4) [DELETE](#del)
		5) [ALTER TABLE](#alttb)
	4. [Aggregate functions](#agg)
		1) [COUNT](#count)
		2) [SUM](#sum)
		3) [AVG](#avg)
		4) [MIN](#min)
		5) [MAX](#max)
		6) [GROUP BY](#groupby)
		7) [HAVING](#having)
		8) [ORDERED BY](#orderedby)
		9) [DESC](#desc)
		10) [OFFSET](#offset)
		11) [FETCH](#fetch)
	5. [JOINS (INNER, LEFT, RIGHT, FULL)](#joins)
	 	1) [JOIN](#joins)
	 	2) [INNER JOIN](#injoin)
	 	3) [LEFT JOIN](#ljoin)
	 	4) [RIGHT JOIN](#rjoin)
	 	5) [FULL JOIN](#fjoin)
	 	6) [EXISTS](#exists)
	 	7) [UNION](#union)
	 6. [Saving](#save)
	 	1) [GRANT](#grant)
	 	2) [REVOKE](#revoke)
	 	3) [SAVEPOINT](#savepoint)
	 	4) [COMMIT](#commit)
	 	5) [ROLLBACK](#rollback)
	 	6) [TRUNCATE](#truncate)
 	 7. [Extras](#extras)
    

---
# Examples <a name="eg"/> 
```sql
SELECT * FROM rental WHERE customer_id IN *
SELECT customer_id
FROM customer
WHERE first_name='MARY')
```
```sql
SELECT *
FROM actor
WHERE LEFT(first_name,1) = 'P';
```
```sql
SELECT CONCAT(fist_name, ' ', last_name) AS name,
LENGTH(CONCAT(first_name, ' ', last_name)) AS len
from actor
Where LENGTH(CONCAT(first_name, ' ', last_name))>17
ORDER BY len DESC
```  
---
# Rules for better schema <a name="schema"/> 
A SQL schema is a useful database concept. It helps us to create a logical grouping of objects such as tables, stored procedures, and functions.
https://www.sisense.com/blog/better-sql-schema/

#### 1. Only Use Lowercase Letters, Numbers, and Underscores
#### 2. Use Simple, Descriptive Column Names
#### 3. Use Simple, Descriptive Table Names
#### 4. Have an Integer Primary Key
#### 5. Be Consistent with Foreign Keys
#### 6. Store Datetimes as Datetimes
#### 7. UTC, Always UTC
#### 8. Have One Source of Truth
#### 9. Prefer Tall Tables without JSON Columns
#### 10. Don’t Over-Normalize
 
##
Primary key
Foreign key

## Commands <a name="commands"/> 

### SELECT <a name="select"/>
Defines the data the query will return.
```sql
-- Specify a column from a table
SELECT column FROM table;
```
```sql
-- Return all columns from table
SELECT * FROM table;
```
#### FROM <a name="from"/>
Specifies the table to pull data from
```sql
SELECT column FROM table;
```
#### DISTINCT <a name="dist"/>
Only returns unique records (removes duplicates)
```sql
SELECT DISTINCT column FROM table;
```
#### INTO <a name="into"/>
Copies the specified data (from one table into another)
```sql
SELECT * INTO new_table FROM old_table;
```
Can also use this to insert new entries
```sql
INSERT INTO table_name(specify, the, columns) VALUES(data, to, add)
```
#### TOP <a name="top"/>
Selects the top x number from the table
```sql
-- x is number
SELECT TOP 50 * FROM table;
```
```sql
-- x is %
SELECT TOP 50 PERCENT * FROM table;
```
##### AS <a name="as"/>
Uses a specified alias for the selected column/table 
```sql
SELECT column AS column_alias FROM table as table_alias
```
---
### WHERE <a name="where"/>
Filters the query for a set condition using operators {=, >, <, >=, <=, etc.}
```sql
-- INT version
SELECT column FROM table WHERE x > 0;
```
```sql
-- String version
SELECT column FROM table WHERE column = 'xyz'
```
#### AND <a name="and"/>
Combines multiple conditions in a single query where ALL must be met
```sql
SELECT column FROM table WHERE column = ‘XYZ’ AND column2 > 15;
```
#### OR <a name="or"/>
Combines multiple conditions in a single query where only ONE condition needs to be met
```sql
SELECT column FROM table WHERE column = ‘XYZ’ OR column2 > 15;
```
#### BETWEEN <a name="between"/>
Filters the query to return results that fit between the specified range
```sql
SELECT column FROM table WHERE column BETWEEN 0 AND 100;
```
#### LIKE <a name="like"/>
Searches for a specified pattern in a column
- %x : will select all values that begin with x
- %x% : will select all values that include x
- x% : will select all values that end with x
- x%y : will select all values that begin with x and end with y
- _x% : will select all values have x as the second character
- x_% : will select all values that begin with x and are at least two characters long. You can add additional _ characters to extend the length requirement, i.e. x___%
- %[0-9]% : wildcard for a number between 0-9
```sql
SELECT column FROM table WHERE column LIKE '%Bob%'
```
#### IN <a name="in"/>
Allows multiple specifications for WHERE command
```sql
SELECT column FROM table WHERE column IN ('X','Y','Z');
```
#### IS NULL <a name="isnull"/>
Only returns rows with a **NULL** value
```sql
SELECT column FROM table WHERE column IS NULL
```
#### IS NOT NULL <a name="notnull"/>
Only returns rows *without* a NULL value
```sql
SELECT column FROM table WHERE column IS NOT NULL
```
---
### CREATE <a name="create"/>
Used to set up a database, table, index or view
#### CREATE DATABASE <a name="db"/>
User running the command must have correct admin rights
```sql
CREATE DATABASE database_name;
```
#### CREATE TABLE <a name="table"/>
Needs to specify the data type (after the name of each column)
- INT: interger
- VARCHAR(50): string with length 50
- DECIMAL(p,s): P=precision is total number of digits saved, S=scale is the number of digits after the decimal
```sql
CREATE TABLE table_name (
    id INT,
    name varchar(255),
    height DECIMAL(5,2)
);
```
**Constraints**
- PRIMARY KEY: cannot contain null
- UNIQUE: cannot contain duplicates but can contain a single NULL
- NOT NULL: no null values
- DEFAULT: specify default value for NULL ('enter value' that must match specified data type)
#### CREATE INDEX <a name="index"/>
Generates an index for a table for faster data retreival
```sql
CREATE INDEX idx_name ON table_name (column1, column2, ...);
```
#### CREATE VIEW<a name="view"/>
Generates a virtual table based on the results of an SQL statement. *like regular table but **not saved***
```sql
CREATE VIEW [View name] AS
SELECT column1, column2
FROM table
WHERE column1 = 'XYZ';
```
---
### DROP <a name="drop"/>
Used to delete entire databases, tables or indexes (only use when absolutely necessary)
#### DROP DATABASE<a name="dropdb"/>
Deletes the entire database including all the tables, indexes etc.
```sql
DROP DATABASE db_name;
```
#### DROP TABLE <a name="droptb"/>
Deletes a table as well as the data within it.
```sql
DROP TABLE table_name;
```
#### DROP INDEX <a name="dropidx"/>
Deletes an index within a database.
```sql
DROP INDEX idx_name;
```
#### DELETE <a name="del"/>
Used to remove all rows, *or **WHERE** clause can be used to delete specified rows*
```sql
DELETE FROM customers
WHERE name = ‘Bob’;
```
#### ALTER TABLE <a name="alttb"/>
Allows columns to be added or removed from a table
```sql
-- adding
ALTER TABLE table_name
ADD column_name VARCHAR(255);
-- removing
ALTER TABLE table_name
DROP COLUMN column_name;
```
---
### Aggregate functions <a name="agg"/>
Performs a calculation on a set of values and returns a single result.
#### COUNT <a name="count"/>
Returns the **number** of rows that match the specified criteria
```sql
-- count all
SELECT COUNT(*)
FROM table_name;
```
#### SUM <a name="sum"/>
Returns the total sum of a numeric column.
```sql
SELECT SUM(variable_name)
FROM table_name;
```
#### AVG <a name="avg"/>
Returns the average value of a numeric column.
```sql
SELECT AVG(variable_name)
FROM table_name;
```
#### MIN <a name="min"/>
Returns the minimum value of a numeric column.
```sql
SELECT MIN(variable_name)
FROM table_name;
```
#### MAX <a name="max"/>
Returns the maximum value of a numeric column.
```sql
SELECT MAX(variable_name)
FROM table_name;
```
#### GROUP BY <a name="groupby"/>
Groups rows with the same values into summary rows. The statement is often used with aggregate functions.
```sql
SELECT column_name, AVG(nvariable)
FROM table_name
GROUP BY column_name;
```
#### HAVING <a name="having"/>
Performs the same action as the WHERE clause but HAVING is used for aggregate functions, because WHERE doesn’t work with them.

The below example would return the number of rows for each name, but only for names with more than 2 records.
```sql
SELECT COUNT(customer_id), name
FROM customers
GROUP BY name
HAVING COUNT(customer_id) > 2;
```
#### ORDERED BY <a name="orderedby"/>
Sets the order of the returned results. *The order will be ascending by default.*
```sql
SELECT variable_name1
FROM table_name
ORDER BY variable_name2;
```
#### DESC <a name="desc"/>
Return the results in descending order.
```sql
SELECT variable_name1
FROM table_name
ORDER BY variable_name2 DESC;
```
#### OFFSET <a name="offset"/>
Works with **ORDER BY** and specifies the number of rows to skip before starting to return rows from the query.
```sql
SELECT variable_name1
FROM table_name
ORDER BY variable_name2
OFFSET 10 ROWS;
```
#### FETCH <a name="fetch"/>
specifies the number of rows to return after the OFFSET clause has been processed. *The OFFSET clause is mandatory, while the FETCH clause is optional*.
```sql
SELECT variable_name1
FROM table_name
ORDER BY variable_name2
OFFSET 10 ROWS
FETCH NEXT 10 ROWS ONLY;
```
---
### JOINS (INNER, LEFT, RIGHT, FULL) <a name="joins"/>
*JOIN* clause is used to combine rows from two or more tables. The four types of JOIN are INNER, LEFT, RIGHT and FULL.
>- **INNER JOIN**: returns rows when there is a match in both tables.
>- **LEFT JOIN**: returns all rows from the left table, even if there are no matches in the right table.
>- **RIGHT JOIN**: returns all rows from the right table, even if there are no matches in the left table.
>- **FULL JOIN**: combines the results of both left and right outer joins.
The joined table will contain all records from both the tables and fill in NULLs for missing matches on either side.
>- **SELF JOIN**: joins a table to itself as if the table were two tables, temporarily renaming at least one table in the SQL statement.
>- **CARTESIAN JOIN**: returns the Cartesian product of the sets of records from the two or more joined tables.

#### INNER JOIN <a name="injoin"/>
INNER JOIN selects records that have matching values in both tables.
```sql
SELECT variable_name1
FROM table_name1
INNER JOIN table_name2
ON table_name1.variable_name = table_name2.variable_name;
```
#### LEFT JOIN <a name="ljoin"/>
Selects records from the left table that match records in the right table.
```sql
SELECT variable_name
FROM left_table
LEFT JOIN right_table
ON left_table.matching_idx = right_table.matching_idx;
```
#### RIGHT JOIN <a name="rjoin"/>
Selects records from the right table that match records in the left table.
```sql
SELECT variable_name
FROM left_table
RIGHT JOIN right_table
ON left_table.matching_idx = right_table.matching_idx;
```
#### FULL JOIN <a name="fjoin"/>
Selects records that have a match in the left **or** right table. (*the “OR” JOIN compared with the “AND” JOIN (INNER JOIN)*).
```sql
SELECT variable_name
FROM left_table
FULL OUTER JOIN right_table
ON left_table.matching_idx = right_table.matching_idx;
```
#### EXISTS <a name="exists"/>
Used to test for the existence of any record in a subquery.
```sql
SELECT variable_name
FROM left_table
WHERE EXISTS
(SELECT x FROM right_table  WHERE idx = 1);
```
#### UNION <a name="union"/>
Combines multiple result-sets using two or more SELECT statements and eliminates duplicate rows.
```sql
SELECT var FROM table1 
UNION
SELECT var FROM table2;
```
---
### Saving <a name="save"/>
Different ways to exercise version control
#### GRANT <a name="grant"/>
Gives a particular user access to database objects such as tables, views or the database itself.
```sql
GRANT SELECT, UPDATE ON table_name TO user_name;
```
#### REVOKE <a name="revoke"/>
Removes a user’s permissions for a particular database object.
```sql
REVOKE SELECT, UPDATE ON table_name FROM user_name;
```
#### SAVEPOINT <a name="savepoint"/>
Allows you to identify a point in a transaction to which you can later roll back. *Similar to creating a backup/checkpoint*.
```sql
SAVEPOINT savepoint_name;
```
#### COMMIT <a name="commit"/>
For saving every transaction to the database. A COMMIT statement will release any existing savepoints that may be in use and once the statement is issued, you cannot roll back the transaction.
```sql
SAVEPOINT savepoint_name;
```
#### ROLLBACK <a name="rollback"/>
Used to undo transactions which are not saved to the database. *This can only be used to undo transactions since the last **COMMIT** or **ROLLBACK** command was issued. You can also rollback to a **SAVEPOINT** that has been created before*.
```sql
ROLLBACK TO savepoint_name;
```
#### TRUNCATE <a name="truncate"/>
Removes all data entries from a table in a database, but keeps the table and structure in place. *Similar to **DELETE***.
```sql
TRUNCATE TABLE table_name;
```
---
### Extras <a name="extras"/>

Converts date/time to string format
```sql
TO_CHAR( value [, format_mask] [, nls_language] )

format(getdate(),'MM/dd/yyyy hh:mm tt')
```

---
