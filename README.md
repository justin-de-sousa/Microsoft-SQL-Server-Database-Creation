<h1>SQL Server Database Creation</h1>

<h2>Summary</h2>
The goal of this project was to create database in Microsoft SQL Server. Creating a good database requires tailoring the structure to meet the usecase, so for this project the usecase the database was designed for would be replacing the paper system of a fictional animal grooming salon called Mr. Bo Jangles. The new system was designed to manage customer data, employee records, appointment scheduling, and service details efficiently. In order to ensure the database would maintain data integrity, quality, scalability, and functionality the database utilized the principles of normalization.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Microsoft SQL Server</b> 
- <b>Lucid Chart</b>

<h2>Project walk-through:</h2>

**Situational Overview:**

Mr. Bo Jangles, a pet grooming salon, needs an electronic database to contain all of their information. The database needs to handle information about: pets; owners; services offered; pricing; transaction records; employees, payroll; and pay statements. The database should also automate the pricing calculations which are based on the weight and height of the pet as well as any additional services requested. 
________________________________________
**Designing Database Structure:**

Before programming the database into SQL, it is important to visualize what the table structure will look like, what information should be grouped together in a table, and what tables should be able to reference each other for future queries. The structure can be visually represented using an entity relationship diagram(ERD). While designing the structure, we focused on balancing functionality with normalization. The rules of normalization are important for maintaining data integrity and quality but over-normalized databases can lose functionality due to the increase in query complexity required to pull information. It is important to note this was actually an interactive process because although we built an initial ERD as we went to implement it in SQL and add functionality it was clear there were necessary modifications required. 

![ERD Diagram](https://raw.githubusercontent.com/justin-de-sousa/Archive/Assets/Microsoft-SQL-Server-Database-Creation/ERD.png)

 ________________________________________
**Correlation Analysis Visualizations** 

![top10corr_descriptions](https://github.com/samgeles/HousingFirst-AU/assets/143467895/b0cb52dd-fa56-4148-b52c-9a20132f1719)

![top10correlations](https://github.com/samgeles/HousingFirst-AU/assets/143467895/1c213ec9-9166-4e30-ba62-f13fb2ed6bf2)

________________________________________
**LDA Visualizations**

![LDA_results](https://github.com/samgeles/HousingFirst-AU/assets/143467895/040e0191-1961-4734-bbfc-cdbfadaa42fe)

![TopicPrevalenceBarChart](https://github.com/samgeles/HousingFirst-AU/assets/143467895/3b853e5e-657a-4d06-9b6d-bb801012dac2)

![TopicDistPieChart](https://github.com/samgeles/HousingFirst-AU/assets/143467895/579d7e3c-a65b-4595-844e-3a703d67428f)

________________________________________
**Maintenance Data Analysis** 

![Vis 1](https://github.com/samgeles/HousingFirst-AU/assets/143467895/8c7adf8b-ea1f-4114-a92a-d3ecacba27c4)

![Vis 2](https://github.com/samgeles/HousingFirst-AU/assets/143467895/38718bb7-b764-43d0-a98e-6e36fe3ab11e)

![Vis 3](https://github.com/samgeles/HousingFirst-AU/assets/143467895/d8cc4a1e-88e2-4de7-bb35-12ef7b1e0d2f)





