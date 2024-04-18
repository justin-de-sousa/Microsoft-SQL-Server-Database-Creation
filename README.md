<h1>SQL Server Database Creation</h1>

<h2>Summary</h2>
The goal of this project was to create a database in Microsoft SQL Server. The database’s design would be tailored to fitting the needs of a fictional pet grooming salon called Mr. BoJangles. This premise will serve as a means to incorporate different types of data a business would need to track and the necessary design structure for a database to be both functional and scalable. The system was designed to manage customer data, employee records, appointment scheduling, and service details efficiently. Additionally, the database incorporated functionions and triggers for automated pricing calculations and comprehensive business insights through strategic querying, which greatly enhanced the operational capabilities of the database.

<br />

<h2>Skills Learned</h2>

- Proficiency in Microsoft SQL Server database creation and querying 
- Enhanced knowledge of database design and normalization principles
- Advanced ability to automate Microsoft SQL Server databases using triggers and functions

<h2>Languages and Tools Used</h2>

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

The database is split into 8 tables which are mostly self explanatory when looking at their names and the information they contain. In order to read the diagram it is important to understand crow's feet notation which visually represents how the keys, the unique identifiers of entries in a table, are connecting rows in each table to relevant information contained in other tables. For example, an entry in the “Customer” table’s first value is the CustomerID. The CustomerID is the primary key or unique numerical identifier for that specific customer. Although each customer in the table has an actual name which is recorded in the table, internally the database will use their primary key as the way to identify which customer is which. This primary key will then be used as a foreign key in other  tables which store information related to that customer. Each customer of Mr. Bo Jangles will presumably have at least one pet but it is also possible they have multiple pets. Instead of storing all of the information of their pet in the same table as the customers information we will normalize this information into two separate tables. To ensure that these two groups of information about a customer and their pet(s) are connected in the database, the primary key of the owner/customer (CustomerID) will also be recorded in their pet’s entry in the “Pet” table. This value is called a foreign key when it is recorded in a different table than the original. The use of keys will be crucial later when trying to query information from multiple tables. 
 ________________________________________
 
**Creating the Tables in Microsft SQL Server**

[Link to Table Creation Code](https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/78855b7f0953bdbee4dc3fc51c5eaf07e7481553/Assets/Code/SQL_Table_Creation_Code.txt)

Now that the database structure has been established the next step is coding it into Microsoft SQL Server. Running code in Microsoft SQL Server is done through queries on the SQL Server program. To make it as easy as possible to replicate the SQL code has been broken up and uploaded as txt files with the code associated with the relevant step. The code just needs to be copied and pasted into the SQL query window and then executed. 

<p align="center"><strong>Example of Query Window with Code Ready to be Executed</strong></p>

![Query Window](https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/78855b7f0953bdbee4dc3fc51c5eaf07e7481553/Assets/SQL%20Query%20Window.png)


The main consideration when taking the ERD database design and creating those tables in SQL is the order the tables should be created. In SQL, a table which has a foreign key reference to another table cannot be initialized until the table it references has already been created. For example, the “Customer” table has to be created before the “Pet” table because the “Pet” table references “Customer.” This will also be important when inputting test entries later because a pet cannot have an entry inserted unless the customer associated with the pet has already had their information inserted into the “Customer” table. This restriction on the order data must be inserted is due to constraints placed on foreign and primary keys. Constraints are very useful for maintaining data quality and integrity because it can help mitigate missing or improper data being inserted. If there is certain information that absolutely needs to be included when generating an entry a NOT NULL constraint can be added after the value type of the column value is established. 
 ________________________________________

**Functions and Triggers**

[Link to Functions and Triggers Code](https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/91784d42ac9a270d9de905d57df4e165f4fa8d9b/Assets/Code/SQL%20Create%20Functions%20and%20Triggers%20Code.txt)

One of the goals of the database was to automate the base price calculation for an appointment based on the animal's weight and hair type. This will require the use of triggers and functions which will automatically use the weight and hair type of a pet from their information in the “Pet” table to update the base price value of an “Appointment” table entry. 


<p align="center"><strong>Base Pricing Table</strong></p>

![Base Price Table](https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/40bec08c8c8945e65b453c8f52932fe3847fdcdc/Assets/base_pricing_table.png)

The function to calculate the base price is a fairly simple if statement designed to take a weight and hair type value as a parameter and return the price but in order to make it an automated process within the database the use of triggers will be necessary. A trigger is a type of  stored procedure in SQL which will execute a given event, in this case a function, when a specific event occurs. In this case, the trigger to calculate the base price of an appointment should occur when an entry is inserted into the “Appointment” table. The trigger will use the PetID of an Appointment entry to then pull the pet’s weight and hair type from the PetTable. IT will then use these two pieces of information to call the base price function to automatically fill the base price value of the appointment. 

<p align="center"><strong>Function to Calculate the Base Price</strong></p>
<p align="center">
  <img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/6d7da71c31e93593bca47a9eed4f7a145718b420/Assets/get_base_price_function.png" alt="Get Base Price Function" width="60%"/>
</p>


<p align="center"><strong>Trigger which calls "GetBasePrice" Function when an Appointment Insert Occurs</strong></p>
<p align="center">
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/6d7da71c31e93593bca47a9eed4f7a145718b420/Assets/set_base_price_trigger.png" alt="Set Base Price Trigger" width="80%"/>
</p>

The other part of the pricing process which needs to be automated is additional service pricing being added to the appointments total price. The additional services Mr. Bo Jangles offers can be found in the table below and is stored in the database under the “ServicePricing” table. To make the database as streamlined for an employee as possible the additional services should be automatically summed up and added to the total price of an appointment. To solve this issue without causing redundancy issues, the “AppointmentServices” table was created. This table will only record the service code (ServiceCodeID) of one additional service and the AppointmentID of the appointment it was utilized on (as well as a primary key to identify it of course). 

<p align="center"><strong>Additional Service Pricing Table</strong></p>
<p align="center">
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/be09100c06b8924724f927f4ecc865b9cacde9cd/Assets/additional_service_pricing_table.png" alt="Set Base Price Trigger" width="60%"/>
</p>

This time the function to calculate the additional service price will take an appointment ID as an input and return the cumulative cost of all the additional services booked for that particular appointment. Essentially the function finds all the entries in the “AppointmentServices” table for an appointment using the AppointmentID, finds what the price for each of these appointment service entries should be using an inner join on the ServiceCodeID, and sums them up.

<p align="center"><strong>Function Calculating an Appointment Additonal Service Price</strong></p>
<p align="center"> 
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/bc46f17f585aa76bde6fadaca13b31f6d0c9195f/Assets/additional_service_price_function.png" alt="Set Base Price Trigger" width="80%"/>
</p>

The trigger which will call on this function will activate whenever an entry is inserted into the “AppointmentServices” table. This will ensure that as each additional service for an appointment is inserted into the database the AdditionalServicePrice value in the “Appointment” table will be updated and accurate.

<p align="center"><strong>Trigger which calls "SetAdditionalServicePrice" when an Additional Service is Instered</strong></p>
<p align="center"> 
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/c8fb5b9f7c703f4916d9712da09e98f8bc5a6f58/Assets/additional_service_trigger.png" alt="Set Base Price Trigger" width="80%"/>
</p>

________________________________________

**Data Insertion**

[Link to Data Insertion Code](https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/b8012e0f5865c5e4bc9dd9f633a7a95d5c7e7d09/Assets/Code/SQL_Data_Insertion_Code.txt)

Once the tables were created and the functions and triggers were implemented the database is now ready to have data inserted into the tables. In order to test the database I used python to create entries. In total there I created 12 employees, 100 customers, 100 pets, 200 appointments, and 300 additional service entries. Importing all of these entries required a large amount of insert statements which can be found in the linked code above. Now that entries have been inserted, the database is ready to have queries performed on it for quick data exploration and analysis. 

<p align="center"><strong>Customer table with test entries ready for queries</strong></p>
<p align="center"> 
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/a0284d189ac178a875645056e5ae03d0999a06ee/Assets/example_of_table_with_entries.png" alt="Set Base Price Trigger" width="80%"/>
</p>

________________________________________

**Database Testing and Querying**

The database should now be fully functioning so to make sure everything is working as intended the next step is to try to use the database to answer questions the business would want to know. The first thing to do is make sure the triggers and functions did their job when the appointment and additional service entries were inserted. This can be checked with a query selecting the top 3 customers by number of appointments and looking at all the additional services they used as well as the price recorded for the additional service value. 

<p align="center"><strong>SQL Query checking Triggers and Fuctions</strong></p>
<p align="center"> 
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/7113deb81336778a22061b4ac017523f6053c26b/Assets/query_checking_triggers_functions.png" width="99%"/>
</p>

<p align="center"><strong>Output of Query in SQL</strong></p>
<p align="center"> 
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/7113deb81336778a22061b4ac017523f6053c26b/Assets/Query_1_output.png" width="90%"/>
</p>

The output allows for confirmation of the function and triggers working correctly. The additional service values for “Appointment” table entries is the sum of all the additional services in the “AppointmentServices” table associated with that appointment. The following will not be examples of questions a Bo Jangles employee may want to answer using the database. 

<p align="center"><strong>What clients have not been seen in a year and when were they last seen?</strong></p>

<p align="center">Query Code</p>
<p align="center"> 
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/2285fd75824d33d4584fd1f499b45ff03082f4ed/Assets/query_2_code.png" width="90%"/>
</p>

<p align="center">Query Output</p>
<p align="center"> 
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/2285fd75824d33d4584fd1f499b45ff03082f4ed/Assets/query_2_output.png" width="90%"/>
</p>

<p align="center"><strong>What services were performed on pets most often (by species)?</strong></p>

<p align="center">Query Code</p>
<p align="center"> 
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/2285fd75824d33d4584fd1f499b45ff03082f4ed/Assets/query_3_code.png" width="90%"/>
</p>

<p align="center">Query Output</p>
<p align="center"> 
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/2285fd75824d33d4584fd1f499b45ff03082f4ed/Assets/query_3_output.png" width="80%"/>
</p>

<p align="center"><strong>Which customers have had the same walk-in service performed multiple times?</strong></p>

<p align="center">Query Code</p>
<p align="center"> 
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/2285fd75824d33d4584fd1f499b45ff03082f4ed/Assets/query_4_code.png" width="90%"/>
</p>

<p align="center">Query Output</p>
<p align="center"> 
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/2285fd75824d33d4584fd1f499b45ff03082f4ed/Assets/query_4_output.png" width="80%"/>
</p>

<p align="center"><strong>Who are top 3 employees with the most years of experience?</strong></p>

<p align="center">Query Code</p>
<p align="center"> 
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/3ebefa5682eec2616741832a9560be6085931690/Assets/query_5_code.png" width="80%"/>
</p>

<p align="center">Query Output</p>
<p align="center"> 
<img src="https://github.com/justin-de-sousa/Microsoft-SQL-Server-Database-Creation/blob/3ebefa5682eec2616741832a9560be6085931690/Assets/query_5_output.png" width="80%"/>
</p>
