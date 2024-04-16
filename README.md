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

Before programming the database into SQL, it is important to visualize what the table structure will look like, what information should be grouped together in a table, and what tables should be able to reference each other for future queries. The structure can be visually represented using an entity relationship diagram(ERD). While designing the structure, we focused on balancing functionality with normalization. The rules of normalization are important for maintaining data integrity and quality but over-normalized databases can lose functionality due to the increase in query complexity required to pull information. It is important to note this was actually an interactive process because although we built an initial ERD as we went to implement it in SQL and add functionality it was clear there were necessary modifications required. 


<p align="center"><strong>Final Entity Relationship Diagram in Crows Feet Notation</strong></p>

![ERD Diagram](https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/d87049c543124c5336e1e0a256314333c07bf3b6/Assets/ERD.png)

**Design Explanation**

 ________________________________________
 
