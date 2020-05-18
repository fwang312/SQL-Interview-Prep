## 1. What is Database?
A database is an organized collection of data, stored and retrieved digitally from a remote or local computer system. Databases can be vast and complex, and such databases are developed using fixed design and modeling approaches.

## 2.What is DBMS?
DBMS stands for Database Management System. DBMS is a system software responsible for the creation, retrieval, updation and management of the database. It ensures that our data is consistent, organized and is easily accessible by serving as an interface between the database and its end users or application softwares.

## 3.What is RDBMS? How is it different from DBMS?
RDBMS stands for Relational Database Management System. The key difference here, compared to DBMS, is that RDBMS stores data in the form of a collection of tables and relations can be defined between the common fields of these tables. Most modern database management systems like MySQL, Microsoft SQL Server, Oracle, IBM DB2 and Amazon Redshift are based on RDBMS.

## 4.What is SQL?
SQL stands for Structured Query Language. It is the standard language for relational database management systems. It is especially useful in handling organized data comprised of entities (variables) and relations between different entities of the data.

## 5.What is the difference between SQL and MySQL?
SQL is a standard language for retrieving and manipulating structured databases. On the contrary, MySQL is a relational database management system, like SQL Server, Oracle or IBM DB2, that is used to manage SQL database

## 6. What are Tables and Fields?
A table is an organized collection of data stored in the form of rows and columns. Columns can be categorized as vertical and rows as horizontal. The columns in a table are called fields while the rows can be referred to as records.

## 7.What are Constraints in SQL?
Constraints are used to specify the rules concerning data in the table. It can be applied for single or multiple fields in an SQL table during creation of table or after creationg using the ALTER TABLE command. The constraints are:

* NOT NULL - Restricts NULL value from being inserted into a column.
* CHECK - Verifies that all values in a field satisfy a condition.
* DEFAULT - Automatically assigns a default value if no value has been specified for the field.
* UNIQUE - Ensures unique values to be inserted into the field.
* INDEX - Indexes a field providing faster retrieval of records.
* PRIMARY KEY - Uniquely identifies each record in a table.
* FOREIGN KEY - Ensures referential integrity for a record in another table.

## 8.What is a Primary Key?
The PRIMARY KEY constraint uniquely identifies each row in a table. It must contain UNIQUE values and has an implicit NOT NULL constraint.A table in SQL is strictly restricted to have one and only one primary key, which is comprised of single or multiple fields (columns).

```html
CREATE TABLE Students ( 	 /* Create table with a single field as primary key */
    ID INT NOT NULL
    Name VARCHAR(255)
    PRIMARY KEY (ID)
);

CREATE TABLE Students ( 	 /* Create table with multiple fields as primary key */
    ID INT NOT NULL
    LastName VARCHAR(255)
    FirstName VARCHAR(255) NOT NULL,
    CONSTRAINT PK_Student
    PRIMARY KEY (ID, FirstName)
);

ALTER TABLE Students 	 /* Set a column as primary key */
ADD PRIMARY KEY (ID);

ALTER TABLE Students 	 /* Set multiple columns as primary key */
ADD CONSTRAINT PK_Student 	 /*Naming a Primary Key*/
PRIMARY KEY (ID, FirstName);

```

## 9.What is a UNIQUE constraint?
A UNIQUE constraint ensures that all values in a column are different. This provides uniqueness for the column(s) and helps identify each row uniquely. Unlike primary key, there can be multiple unique constraints defined per table.

```html
CREATE TABLE Students ( 	 /* Create table with a single field as unique */
    ID INT NOT NULL UNIQUE
    Name VARCHAR(255)
);

CREATE TABLE Students ( 	 /* Create table with multiple fields as unique */
    ID INT NOT NULL
    LastName VARCHAR(255)
    FirstName VARCHAR(255) NOT NULL
    CONSTRAINT PK_Student
    UNIQUE (ID, FirstName)
);

ALTER TABLE Students 	 /* Set a column as unique */
ADD UNIQUE (ID);

ALTER TABLE Students 	 /* Set multiple columns as unique */
ADD CONSTRAINT PK_Student 	 /* Naming a unique constraint */
UNIQUE (ID, FirstName);
```

## 10.What is a Foreign Key?
A FOREIGN KEY comprises of single or collection of fields in a table that essentially refer to the PRIMARY KEY in another table. Foreign key constraint ensures referential integrity in the relation between two tables.

The table with the foreign key constraint is labelled as the child table, and the table containing the candidate key is labelled as the referenced or parent table.

```html
CREATE TABLE Students ( 	 /* Create table with foreign key - Way 1 */
    ID INT NOT NULL
    Name VARCHAR(255)
    LibraryID INT
    PRIMARY KEY (ID)
    FOREIGN KEY (Library_ID) REFERENCES Library(LibraryID)
);

CREATE TABLE Students ( 	 /* Create table with foreign key - Way 2 */
    ID INT NOT NULL PRIMARY KEY
    Name VARCHAR(255)
    LibraryID INT FOREIGN KEY (Library_ID) REFERENCES Library(LibraryID)
);


ALTER TABLE Students 	 /* Add a new foreign key */
ADD FOREIGN KEY (LibraryID)
REFERENCES Library (LibraryID);
```

A FOREIGN KEY comprises of single or collection of fields in a table that essentially refer to the PRIMARY KEY in another table. Foreign key constraint ensures referential integrity in the relation between two tables.

## 11. What is a Join? List its different types.
The SQL Join clause is used to combine records (rows) from two or more tables in a SQL database based on a related column between the two.

#### There are four different types of JOINs in SQL:

* (INNER) JOIN: Retrieves records that have matching values in both tables involved in the join. This is the widely used join for queries.
N Table_B;

* LEFT (OUTER) JOIN: Retrieves all the records/rows from the left and the matched records/rows from the right table

* RIGHT (OUTER) JOIN: Retrieves all the records/rows from the right and the matched records/rows from the left table.

* FULL (OUTER) JOIN: Retrieves all the records where there is a match in either the left or right table.

## 12.What is a Self-Join?
A self JOIN is a case of regular join where a table is joined to itself based on some relation between its own column(s). Self-join uses the INNER JOIN or LEFT JOIN clause and a table alias is used to assign different names to the table within the query.

## 13.What is a Cross-Join?
Cross join can be defined as a cartesian product of the two tables included in the join. The table after join contains the same number of rows as in the cross-product of number of rows in the two tables. If a WHERE clause is used in cross join then the query will work like an INNER JOIN.

<img width="845" alt="Self join_Cross join" src="https://user-images.githubusercontent.com/61290493/82003648-7f7c5600-9626-11ea-80fc-6450e96e0587.png">

## 14.What is an Index? Explain its different types.
A database index is a data structure that provides quick lookup of data in a column or columns of a table. It enhances the speed of operations accessing data from a database table at the cost of additional writes and memory to maintain the index data structure.

数据库索引是一种数据结构，可以快速查找表的一个或多个列中的数据。 它以额外的写入和内存维护索引数据结构为代价，提高了从数据库表访问数据的操作速度。

```html
example:
CREATE INDEX index_name 	 /* Create Index */
ON table_name (column_1, column_2);

DROP INDEX index_name; 	 /* Drop Index */
```
There are different types of indexes that can be created for different purposes:
#### Unique and Non-Unique Index:

Unique indexes are indexes that help maintain data integrity by ensuring that no two rows of data in a table have identical key values. Once a unique index has been defined for a table, uniqueness is enforced whenever keys are added or changed within the index.

```html
CREATE UNIQUE INDEX myIndex
ON students (enroll_no);
```
Non-unique indexes, on the other hand, are not used to enforce constraints on the tables with which they are associated. Instead, non-unique indexes are used solely to improve query performance by maintaining a sorted order of data values that are used frequently.

#### Clustered and Non-Clustered Index:
Clustered indexes are indexes whose order of the rows in the database correspond to the order of the rows in the index. This is why only one clustered index can exist in a given table, whereas, multiple non-clustered indexes can exist in the table.

The only difference between clustered and non-clustered indexes is that the database manager attempts to keep the data in the database in the same order as the corresponding keys appear in the clustered index.

Clustering index can improve the performance of most query operations because they provide a linear-access path to data stored in the database.

## 15.What is the difference between Clustered and Non-clustered index?
* Clustered index modifies the way records are stored in a database based on the indexed column. Non-clustered index creates a separate entity within the table which references the original table.

* Clustered index is used for easy and speedy retrieval of data from the database, whereas, fetching records from the non-clustered index is relatively slower.

* In SQL, a table can have a single clustered index whereas it can have multiple non-clustered indexes.

## 16. What is Data Integrity?
Data Integrity is the assurance of accuracy and consistency of data over its entire life-cycle, and is a critical aspect to the design, implementation and usage of any database. It also defines integrity constraints to enforce business rules on the data when it is entered into an application or a database.

## 17. What is a Query?
A query is a request for data or information from a database table or combination of tables. A database query can be either a select query or an action query.
```html
SELECT fname, lname 		 /* select query */
FROM myDb.students
WHERE student_id = 1;
UPDATE myDB.students 		 /* action query */
SET fname = 'Captain', lname = 'America'
WHERE student_id = 1;
```

## 18. What is a Subquery? What are its types?
A subquery is a query within another query, also known as nested query or inner query . It is used to restrict or enhance the data to be queried by the main query.

For example, here we fetch the contact information for students who have enrolled for the maths subject:
```html
SELECT name, email, mob, address
FROM myDb.contacts
WHERE roll_no IN (
	 SELECT roll_no
	 FROM myDb.students
	 WHERE subject = 'Maths');
```
##### There are two types of subquery - Correlated and Non-Correlated：

* A correlated subquery cannot be considered as an independent query, but it can refer the column in a table listed in the FROM of the main query.

* A non-correlated subquery can be considered as an independent query and the output of subquery is substituted in the main query.

## 19. What is the SELECT statement?
SELECT operator in SQL is used to select data from a database. The data returned is stored in a result table, called the result-set.

## 20. What are some common clauses used with SELECT query in SQL?
* WHERE clause in SQL is used to filter records that are necessary, based on specific conditions.

* ORDER BY clause in SQL is used to sort the records based on some field(s) in ascending (ASC) or descending order (DESC).
```html
SELECT *
FROM myDB.students
WHERE graduation_year = 2019
ORDER BY studentID DESC;
```
* GROUP BY clause in SQL is used to group records with identical data and can be used in conjuction with some aggregation functions to produce summarized results from the database.

* HAVING clause in SQL is used to filter records in combination with the GROUP BY clause. It is different from WHERE, since WHERE clause cannot filter aggregated records.
```html
SELECT COUNT(studentId), country
FROM myDB.students
WHERE country != "INDIA"
GROUP BY country
HAVING COUNT(studentID) > 5;
```

## 21.What are UNION, MINUS and INTERSECT commands?
* The UNION operator combines and returns the result-set retrieved by two or more SELECT statements.
```html
SELECT name FROM Students 	 /* Fetch the union of queries */
UNION
SELECT name FROM Contacts;

SELECT name FROM Students 	 /* Fetch the union of queries with duplicates*/
UNION ALL
SELECT name FROM Contacts;	
```
* The MINUS operator in SQL is used to remove duplicates from the result-set obtained by the second SELECT query from the result-set obtained by the first SELECT query and then return the filtered results from the first.
```html
SELECT name FROM Students 	 /* Fetch names from students */
MINUS 				/* that aren't present in contacts */
SELECT name FROM Contacts;
```
* The INTERSECT clause in SQL combines the result-set fetched by the two SELECT statements where records from one match the other and then returns this intersection of result-sets.
```html
SELECT name FROM Students 	 /* Fetch names from students */
INTERSECT 			/* that are present in contacts as well */
SELECT name FROM Contacts;
```
## 22.What is Cursor? How to use a Cursor?
A database cursor is a control structure that allows for traversal of records in a database. Cursors, in addition, facilitates processing after traversal, such as retrieval, addition and deletion of database records. They can be viewed as a pointer to one row in a set of rows.

数据库游标是一种控制结构，允许遍历数据库中的记录。 此外，游标还有助于遍历后的处理，例如数据库记录的检索，添加和删除。 可以将它们视为指向一组行中的一行的指针。

##### Working with SQL Cursor
* DECLARE a cursor after any variable declaration. The cursor declaration must always be associated with a SELECT Statement.
* Open cursor to initialize the result set. The OPEN statement must be called before fetching rows from the result set.
* FETCH statement to retrieve and move to the next row in the result set.
* Call the CLOSE statement to deactivate the cursor.
* Finally use the DEALLOCATE statement to delete the cursor definition and release the associated resources.

```html
DECLARE @name VARCHAR(50) 	 /* Declare All Required Variables */

DECLARE db_cursor CURSOR FOR 	 /* Declare Cursor Name*/
SELECT name
FROM myDB.students
WHERE parent_name IN ('Sara', 'Ansh')

OPEN db_cursor 	 /* Open cursor and Fetch data into @name */ 
FETCH next
FROM db_cursor
INTO @name

CLOSE db_cursor 	 /* Close the cursor and deallocate the resources */
DEALLOCATE db_cursor
```
## 23. What are Entities and Relationships?
Entity: An entity can be a real-world object, either tangible or intangible, that can be easily identifiable. For example, in a college database, students, professors, workers, departments, and projects can be referred to as entities. Each entity has some associated properties that provide it an identity.

Relationships: Relations or links between entities that have something to do with each other. For example - The employees table in a company's database can be associated with the salary table in the same database.

## 24.List the different types of relationships in SQL.
* One-to-One - This can be defined as the relationship between two tables where each record in one table is associated with the maximum of one record in the other table.

* One-to-Many & Many-to-One - This is the most commonly used relationship where a record in a table is associated with multiple records in the other table.

* Many-to-Many - This is used in cases when multiple instances on both sides are needed for defining a relationship.

* Self Referencing Relationships - This is used when a table needs to define a relationship with itself.

## 25.What is an Alias in SQL?
An alias is a feature of SQL that is supported by most, if not all, RDBMSs. It is a temporary name assigned to the table or table column for the purpose of a particular SQL query. In addition, aliasing can be employed as an obfuscation technique to secure the real names of database fields. A table alias is also called a correlation name .

An alias is represented explicitly by the AS keyword but in some cases the same can be performed without it as well. Nevertheless, using the AS keyword is always a good practice.
```html
SELECT A.emp_name AS "Employee" 	/* Alias using AS keyword */
B.emp_name AS "Supervisor"
FROM employee A, employee B 		/* Alias without AS keyword */
WHERE A.emp_sup = B.emp_id;
```
## 26. What is a View?
A view in SQL is a virtual table based on the result-set of an SQL statement. A view contains rows and columns, just like a real table. The fields in a view are fields from one or more real tables in the database.

<img width="635" alt="View" src="https://user-images.githubusercontent.com/61290493/82258985-763e0280-9920-11ea-9887-d7e2c2fea449.png">

## 27. What is Normalization?
Normalization represents the way of organizing structured data in the database efficiently. It includes creation of tables, establishing relationships between them, and defining rules for those relationships. Inconsistency and redundancy can be kept in check based on these rules, hence, adding flexibility to the database.

## 28. What is Denormalization?
Denormalization is the inverse process of normalization, where the normalized schema is converted into a schema which has redundant information. The performance is improved by using redundancy and keeping the redundant data consistent. The reason for performing denormalization is the overheads produced in query processor by an over-normalized structure.

## 29.What are the TRUNCATE, DELETE and DROP statements?
* DELETE statement is used to delete rows from a table.
```html
DELETE FROM Candidates
WHERE CandidateId > 1000;
```
* TRUNCATE command is used to delete all the rows from the table and free the space containing the table.
```html
TRUNCATE TABLE Candidates;
```
* DROP command is used to remove an object from the database. If you drop a table, all the rows in the table is deleted and the table structure is removed from the database.
```html
DROP TABLE Candidates;
```
## 30.What is the difference between DROP and TRUNCATE statements?
If a table is dropped, all things associated with the tables are dropped as well. This includes - the relationships defined on the table with other tables, the integrity checks and constraints, access privileges and other grants that the table has. To create and use the table again in its original form, all these relations, checks, constraints, privileges and relationships need to be redefined. 

However, if a table is truncated, none of the above problems exist and the table retains its original structure.

## 32. What is the difference between DELETE and TRUNCATE statements?
The TRUNCATE command is used to delete all the rows from the table and free the space containing the table.

The DELETE command deletes only the rows from the table based on the condition given in the where clause or deletes all the rows from the table if no condition is specified. But it does not free the space containing the table.

## 33.What are Aggregate and Scalar functions?
An aggregate function performs operations on a collection of values to return a single scalar value. Aggregate functions are often used with the GROUP BY and HAVING clauses of the SELECT statement. Following are the widely used SQL aggregate functions:

* AVG() - Calculates the mean of a collection of values.
* COUNT() - Counts the total number of records in a specific table or view.
* MIN() - Calculates the minimum of a collection of values.
* MAX() - Calculates the maximum of a collection of values.
* SUM() - Calculates the sum of a collection of values.
* FIRST() - Fetches the first element in a collection of values.
* LAST() - Fetches the last element in a collection of values.

##### Note: All aggregate functions described above ignore NULL values except for the COUNT function.

A scalar function returns a single value based on the input value. Following are the widely used SQL scalar functions:
* LEN() - Calculates the total length of the given field (column).
* UCASE() - Converts a collection of string values to uppercase characters.
* LCASE() - Converts a collection of string values to lowercase characters.
* MID() - Extracts substrings from a collection of string values in a table.
* CONCAT() - Concatenates two or more strings.
* RAND() - Generates a random collection of numbers of given length.
* ROUND() - Calculates the round off integer value for a numeric field (or decimal point values).
* NOW() - Returns the current data & time.
* FORMAT() - Sets the format to display a collection of values.
