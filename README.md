<h1>SQL Server Database Creation</h1>

<h2>Summary</h2>
The goal of this project was to create database in Microsoft SQL Server. Creating a good database requires tailoring the structure to meet the usecase, so for this project the usecase the database was designed for would be replacing the paper system of a fictional animal grooming salon called Mr. Bo Jangles. The new system was designed to manage customer data, employee records, appointment scheduling, and service details efficiently. In order to ensure the database would maintain data integrity, quality, scalability, and functionality the database utilized the principles of normalization.
<br />

<h2>Skills Learned</h2>

- Proficiency in Microsoft SQL Server database creation and querying 
- Enhanced knowledge of database design and normalization principles
- Advanced ability to automate Microsoft SQL Server databases using triggers and functions

<h2>Languages and Utilities Used</h2>

- <b>Microsoft SQL Server</b> 
- <b>Lucid Chart</b>

<h2>Project walk-through:</h2>

**Situational Overview**

Mr. Bo Jangles, a pet grooming salon, needs an electronic database to contain all of their information. The database needs to handle information about: pets; owners; services offered; pricing; transaction records; employees, payroll; and pay statements. The database should also automate the pricing calculations which are based on the weight and height of the pet as well as any additional services requested. 
________________________________________
**Designing Database Structure**

Before programming the database into SQL, it is important to visualize what the table structure will look like, what information should be grouped together in a table, what type of value a piece of information should be stored as, and what tables should be able to reference each other for future queries. The structure can be visually represented using an entity relationship diagram(ERD). While designing the structure, we focused on balancing functionality with normalization. The rules of normalization are important for maintaining data integrity and quality but over-normalized databases can lose functionality due to the increase in query complexity required to pull information. It is important to note this was actually an interactive process because although we built an initial ERD as we went to implement it in SQL and add functionality it was clear there were necessary modifications required. 


<p align="center"><strong>Final Entity Relationship Diagram in Crows Feet Notation</strong></p>

![ERD Diagram](https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/d87049c543124c5336e1e0a256314333c07bf3b6/Assets/ERD.png)

**Design Explanation**

The database is split into 8 tables which are mostly self explanatory when looking at their names and the information they contain. In order to read the diagram it is important to understand crow's feet notation which visually represents how the keys, the unique identifiers of entries in a table, are connecting rows in each table to relevant information contained in other tables. For example, an entry in the “Customer” table’s first value is the CustomerID. The CustomerID is the primary key or unique numerical identifier for that specific customer. Although each customer in the table has an actual name which is recorded in the table, internally the database will use their primary key as the way to identify which customer is which. This primary key will then be used as a foreign key in other  tables which store information related to that customer. Each customer of Mr. BoJangles will presumably have at least one pet but it is also possible they have multiple pets. Instead of storing all of the information of their pet in the same table as the customers information we will normalize this information into two separate tables. To ensure that these two groups of information about a customer and their pet(s) are connected in the database, the primary key of the owner/customer (CustomerID) will also be recorded in their pet’s entry in the “Pet” table. This value is called a foreign key when it is recorded in a different table than the original. The use of keys will be crucial later when trying to query information from multiple tables. 
 ________________________________________
 
**Creating the Tables in Microsft SQL Server**

[Link to Table Creation Code](https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/78855b7f0953bdbee4dc3fc51c5eaf07e7481553/Assets/Code/SQL_Table_Creation_Code.txt)

Now that the database structure has been established the next step is coding it into Microsoft SQL Server. Running code in Microsoft SQL Server is done through queries on the SQL Server program. To make it as easy as possible to replicate the SQL code has been broken up and uploaded as txt files with the code associated with the relevant step. The code just needs to be copied and pasted into the SQL query window and then executed. 

<p align="center"><strong>Example of Query Window with Code Ready to be Executed</strong></p>

![Query Window](https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/78855b7f0953bdbee4dc3fc51c5eaf07e7481553/Assets/SQL%20Query%20Window.png)


The main consideration when taking the ERD database design and creating those tables in SQL is the order the tables should be created. In SQL, a table which has a foreign key reference to another table cannot be initialized until the table it references has already been created. For example, the “Customer” table has to be created before the “Pet” table because the “Pet” table references “Customer.” This will also be important when inputting test entries later because a pet cannot have an entry inserted unless the customer associated with the pet has already had their information inserted into the “Customer” table. This restriction on the order data must be inserted is due to constraints placed on foreign and primary keys. Constraints are very useful for maintaining data quality and integrity because it can help mitigate missing or improper data being inserted. If there is certain information that absolutely needs to be included when generating an entry a NOT NULL constraint can be added after the value type of the column value is established. 
 ________________________________________

**Functions and Triggers**


