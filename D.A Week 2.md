# Module 2: Data Preparation and Exploration

In this module, we will:

  * Understand how to explore and acquire data.
    
  * Learn about databases and the need to classify and store or structure data.

  * Compare various data manipulation techniques and how to manage data quality.

  * Explain the fundamentals of statistics and analysis techniques.

    
# Chapter 3: Databases and Data Acquisition


# Databases and Data Acquisition

In this chapter: 

  * Data concepts and environment

  * Identify basic concepts of data schemas and dimensions.

  * Understanding the domain of data mining.

  * Explain data acquisition concepts.

  * Explain common techniques for data manipulation and query optimization.

There are many different databases options to choose from when an organization needs to store data.

1. Relational

2. Nonrelational


*The Relational Model* 

The relational model builds on the concept of tabular data. In the relational model, an entity contains data for a single subject. When creating an IT System, you need to consider all the entities required to make your system work.

The Entity Relationship Diagram  (ERD) is a visual artifact of the data modeling process. It shows the connection between related entities. A relationship is a connection between entities, the symbols adjacent to an entity describe the relationship.

Cardinality is the relationship between two entities, showing how many instances of one entity relate to instances of another entity. You specify the cardinality in an ERD with various line endings. 

The first component of the terminator indicates whether the relationship between the two entities is optional or required.

The second components indicates whether an entity instance in the first table is associated with a single entity instance in the related table or if an association can exist with multiple entity instances.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/441935d7-c360-48c2-96a7-8eef95e87ee8)

When reading from an ER Diagram aloud from left to right, you say "An individual animal belongs to at least one and possibly many people". Reading from right to left, you say "A specific person has at least one and possibly many animals".

Unary relationship is when an entity has a connection with itself. e.g a single manager has multiple employees.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/1505e022-25b5-4775-9c78-32288a85a767)


A binary relationship connects two entities. They are the most common and easy to explore whereas a unary and ternary are comparatively complex and rare.

A ternary relationship connects three entities.

Apart from being a helpful picture, the entity relationship diagram also serves as a relational database's blueprint. The ability to read ERDs helps you understand the structure of a relational database.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/03a68e3c-3576-4f39-a303-c3ab72e694fe)

*Relational Databases*

Pieces of software that let you make an operational system out of an ERD. You start with a relational model and create a physical design. Relational entities correspond to databse tables and entuty attributes correspond to table columns. 

When creating a database table, the ordering of columns does not matter because you can specify the column order when retrieving the data from a table. When attributes becomes a column, you assign it a data type. 

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/94c311de-f1f6-4f5c-9507-80a7dea0a80b)

In the above figure, a new table was created. AnimalPerson is necessary because you need to resolve a many-to-many relationship with an associative table. 

An associative table is both a table and a relationship. An associative table lets you identify the relationship between a specific animal and a particular person with a minimum amount of data duplication. 

Relational databases are complicated to operate at scale. A database admin is a highly trained person who understands how database software interacts with computer hardware. They look after how the database uses the underlying storage, memory and processor resource assigned to the database. Also looks for processes that are slowing down the database down.

**NonRelational Databases**

Do not have a predefined structure based on tabular data. Highly flexible approach in storing data. 

Data types available in relational databases are absent. Data validation happens in code.

*Key-Value*

* Simple data storage: Data is stored as key-value pairs, offering a straightforward approach.

* Unique keys: each key acts as a unique identifier for its corresponding value within the entire database. 

* Flexible values: Values can be various data types, structured or unstructured, providing versatility.

* Simpler operation: absence of complex table structures makes key-value databases easier to manage compared to relational databases.

* Scalability: Handle numerous concurrent requests efficientl , making them suitable for large-scale applications.

* Limited search: searching relies solely on the key value, as there are no pre-defined structures to query accross.

*Document*

It is similar to key-value database, with additional restrictions. 

* Similar to key-value stores, but structured: Like key-value databases, documents are accessed using unique keys. However, document databases add a layer of structure to the values.

* Structured values: Document databases enforce a specific format on the values, such as JSON or XML. This structure allows for more advanced capabilities.

* Flexibility beyond key-value: While key-value stores only allow searching by key, document databases enable searching within the document itself due to the structured format.

* Example: Social network profiles: Imagine storing profiles as JSON documents with a username as the key. The document value would contain details like zip code. You can then search for profiles in a specific zip code because the database understands the structure and can search within documents.

*Column-Family*

* Group related columns together.

* Indexing: Use an index to efficiently locate data within column families.

* Scalability: Allows for distributing data across multiple machines, making them perfect for handling massive datasets.

* Performance: excel at tasks that involve examining specific columns across many rows.

*Graphs*

* Graph databases excel at capturing and exploring connections between data points.

* Nodes & Properties: Data in a graph is represented as Nodes(entities) that can have properties containing specific attributes.

* Relationships: Edges or arrows connect nodes, depicting the relationships between them.

* Graphs offer a more streamlined approach to navigate connections.

***Database Use Cases***

Business requirements impact the design of individual tables and how they are interconnected. Transactional and reporting systems need different implementation approaches to serve the people who use them efficiently. Databases tend to support two major categories of data processing: Online Transactional Processing(OLTP) and Online Analytical Processing (OLAP).

**Online Transactional Processing**

This system handles the transactions we encounter everyday. While the number of transactions a system handles on a given day can be very high, individual transactions process small amounts of data. OLTP systems balance the ability to write and read data efficiently.

**Normalization**

* organize data in a database efficiently, to minimize redundancy and imporve data integrity.

It reduces wasted storage space by eliminating duplicate data. Improves data accuracy by preventing inconsistencies. Enhances query performance by making data easier to retrieve and manipulate.

*Normalization levels(1NF, 2NF, 3NF)*

* First Normal Form(1NF)
  
  * Each table row is unique (Identified by a primary key).
 
  * Every column has a single value(no repeating groups of values within cell)

* Second Normal Form (2NF)
   
  * Meets all requirements of 1NF.
  
  * Eliminates partial dependencies. Every non-key column must depend on the entire primary key, not just a part of it.

* Third Normal Form (3NF)

  * Meets all requirements of 2NF.
 
  * Eliminates transitive dependencies. No columns depend on each other indirectly through another column. they should rely on the primary key.

**Online Analytical Processing**

OLAP systems focus on the ability of organizations to analyze data. OLTP databases need to balance transactional read and write performance, resulting in a highly normalized design.

OLAP systems have a denormalized design. Instead of having data distributed across multiple tables, denormalization results in wider tables than those found in an OLTP database.

It is more efficient for analytical queries to read large amounts of data for a single table instead of incurring the cost of joining multiple tables together. 

**Schema Concepts**

Its design depends on the purpose it serves. Transactional systems require highly normalized databases.

A data warehouse - a database that aggregates data from many transactional systems for analytical purposes. 

Transactional data may come from systems that power the human resources, sales, marketing and product divisions. 

A data warehouse facilitates analytics across the entire company. 

Data Mart - is a subset of a data warehouse.

The data warehouse serves the entire organization, the data mart focuses on the needs of a particular department within the organization.

Data lake stores raw data in its native format instead of conforming to a relational database structure. Using a data lake is more complex than a data warehouse or data mart. It requires additional knowledge about raw data to make it analytically useful. Relational databases enforces a structure that encapsulates business rules and business logic, both of which are missing in a data lake.

There are 3 main types of databases: 

* Transactional Systems: These are for everyday tasks like sales,or human resource. They need to be organized and accurate.

* Data warehouse: These are for analyzing data from many sources like sales, marketing and human resources. They are good for understanding trends across the company.

* Data marts: These are like smaller versions of data warehouses, but they focus on the needs of one department like human resources.

Data lakes are different because they store raw data instead of organizing it in a neat way.

When designing a database, consider how you will use the data and how much data you will have.

Star and Snowflake are two ways to organize data specifically for data wwarehouses, which store information for analysis

Star schema: simple, like a well-organized shelf of a library. It has the central fact table with key metrics surrounded by dimension tables. These dimension tables contain details that categorize the fact.

Snowflake Schema: More complex, like a library with many subcategories. similar to star schema, but dimension tables thrmselves are broken down into further details.

**Dimensionality**

* refers to how many attributes a table has(can hold). More details means higher dimensionality.

Dimension Tables:

These tables provide context for the data in another table (usually a fact table).

They contain details that categorize the main data points.

Think of them as chapters or sections that explain the "what" in the main story (fact table).


***Data Acquisition Concepts***

**Integration**

Data from transactional systems flows into data warehouses and data marts for analysis.OLTP & OLAP databases have different internal structures, you need to retrieve, reshape and insert data to move data between operational and analytical environments. You can use different methods to transfer data efficiently and effectively.

ETL:

* Extract: first phase, you extract data from the source system and place it in a staging area. The goal of the extract phase is to move data from a relational database to a flat file as quickly as possible.

* Transform: second phase is to transform the data. The goal is to reformat the data from its transactional structure to the data warehouse's analytical design.

* Load: The purpose of the phase is to ensure that data gets into the analytical system as quickly as possible.

ELT (Extract, Load and Transform) is a varient of ETL. With ELT, data is extracted from a source database and loaded directly into the data warehouse. Once the extract and load phase are complete, the transformation phase gets underway. one key difference between ETL and ELT is the technical component performing the transformation. with ETL, data transformation takes place external to a relational database, using a programming language like Python. ELT uses SQL and the power of relational database to reformat the data.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/57df19c9-2bbe-4f1c-84c5-f2be5784e041)

***Data Collection Methods***

Augmenting data from your transactional systems with external data is an excellent way to improve the analytical capabilities of your organization.

An API is a structured method for computer systems to exchange information. The internal structure does not matter as long as the API return the data you want. APIs can be transactional, returning data as JSON objects. APIs can also facilitate bulk data extraction returning CSV files.

APIs represent a specific piece of business functionality. 

***Web Services***

A web service is an API you can call via HyperText Transfer Protocol(HTTP), the language of the World Wide Web.


***Web Scraping***

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/8879b523-bab9-49a7-8917-6dffda77deaf)

***Human-in-the-loop***

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/b181bb86-d92a-4bc7-b6e2-8a1bde47d77d)

***Surveys***

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/a1d64f18-fd39-436a-8f1d-f6bb66d98677)


***Obserbation***

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/f68bac82-6197-40dd-8e06-0425cf81c8e9)

***Sampling***

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/78aa958d-43de-4416-838b-5bc1279ea8de)

**Working with Data**

Determine the right database structure, identifying the data sources and loading a database takes a considerable amount of effort. To turn it into an operational database ready to accept data, you use the Data Definition Language (DDL) components of SQL. DDL lets you create, modify and delete tabkes and other associated database objects. To generate insights, a productive analyst must be comfortable using Data Manipulation Language capabilities of SQL to insert, modify and retrieve information from databases. DDL manages the structure of the database, DML manages the data in the database.

**Data Manipulation**

When manipulating data, 4 possible actions occur:
  1. Create new data.

  2. Read existing data.

  3. Update existing data.

  4. Delete existing data.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/f96e9c01-bf37-4320-a088-1d1170e4e035)

**SQL Considerations**

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/52507a94-55b5-41b5-80e7-75a5a82c6e61)

**Filtering**

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/1b048348-61b0-49a0-9df9-65e6fb87f814)

**Filtering and Logical Operators**

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/0a17e30d-2fc1-4a4c-a446-a10e293763d5)

complex queries frequently use multiple logical operators at the same time. Data warehouse often contains millions, billions or even trillions of individual data records. Filtering data is essential to making effective use of these massive data stores.

**Sorting**

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/8e9dd2e9-9583-4464-b577-3d94fd0188a7)

**Data Functions**

Date columns also appear in transactional systems. Storing data information about an event facilitates analysis across time. The most thing is that you have to understand the database platform you are using and how that platform handles dates and time.

**Logical Functions**

They are like tools you can use in your queries to narrow down or manipulate your search results. They act like decision makers, using keywords like AND, OR, NOT to compare data and determine which rows to include in the answer.

**Aggregate Functions**

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/e93cb524-ab1a-4a56-9f40-8b403555fbe5)

**System Functions**

Each database offers functions that expose data about the database itself. Frequently used system functions returns the current date. current date is a component of transactional records and enables time-based analysis in the future.. it is also necessary for a system that uses an effective date approach.

They also return data about the database environment.

**Query Optimization**

**Parametrization**

whenever an SQL query is ran, the database needs to translate it from human-readable form to code it understands(machine code). this translation process is called *parsing*.

parsing takes time and the more complex the query, the longer it takes. This can slow down how fast you get results.

Parameterization to the Rescue:

Parameterization is a technique that helps reduce the amount of parsing needed for certain types of queries.

Imagine a website that personalizes greetings based on the user's name.

A bad approach would be to write the name directly into the query (like "SELECT * FROM users WHERE name = 'Gerald'"). This creates a unique query for every user, forcing the database to parse it each time.

Benefits of Parameterization:

Parameterization uses a placeholder (like &customer_name) in the query.

The web server code then inserts the actual user's name (like "Gerald" or "Gina") into the placeholder before sending the query to the database.

From the database's perspective, it sees the same basic query structure every time, regardless of the inserted name.

This significantly reduces parsing overhead, especially for queries that are used repeatedly with different values.

Summary:

Parameterization is a trick to improve the performance of your SQL queries. It treats frequently used queries with variable parts as a single template, reducing the database's workload and speeding up your results.

**Indexing**

Finding data in a database:

Imagine searching for a specific fact in a book. Without an index (like a table of contents), you'd have to flip through every page (full table scan). This is slow for large amounts of data (big books).

Database indexes to the rescue:

Indexes act like a book's index – they point you to the right location (data row) quickly.

They work for single columns or combinations (like finding a specific word or phrase in a book's index).

Optimum performance:

Ideally, all the data you need in your query (SELECT statement) should be included in the index, like having relevant keywords listed in the book's index.

If not all, at least the first column you're searching by (like the first word in a phrase) should be indexed.

Considering indexes:

If your queries are slow, check the table's indexes. Discuss adding new ones with a database administrator (DBA) who can create them and consider other performance factors.

Trade-offs:

While indexes speed up searching (reading data), they can slow down adding, updating, or deleting data (writing data) – like having to rewrite the book's index every time you add a new page.

DBA's role:

DBAs decide on indexing strategies considering the database type (transactional for everyday tasks or reporting for analyzing data) to balance speed and efficiency.

Summary:

Database indexes are like book indexes – they help find data fast in large datasets. They have trade-offs but can significantly improve query performance.

**Data Subsets & Temporary Tables**

Large datasets, big problems:

Imagine a data warehouse with billions of rows of order history data.

Analyzing a specific customer's orders from that massive table would be slow and inefficient.

Temporary tables for the rescue:

Temporary tables act like scratchpads for your data analysis.

You can use a query to create a temporary table containing just the relevant data (e.g., a single customer's orders).

You can then run your analysis queries on this smaller, more manageable temporary table.

Temporary and disposable:

Unlike the main data warehouse tables, temporary tables are temporary.

They are automatically deleted when you disconnect from the database, so you don't have to worry about cleaning up.

Use case:

This is ideal for ad hoc analysis, where you need to explore specific data subsets without affecting the main tables.

Summary:

Temporary tables are a handy tool for working with smaller, more focused datasets within a large data warehouse, making your analysis tasks faster and more efficient.

**Execution Plan**

Execution Plans: Behind the Scenes of Your Queries

Imagine you ask a database to retrieve some data. The database follows a specific plan to get that information efficiently.

An execution plan is like a roadmap that shows exactly how the database goes about executing your query.

Why are Execution Plans Important?

Sometimes, queries can run slow. Execution plans help you troubleshoot these issues.

They reveal details about how the database is processing the query, like whether it's scanning the entire table (slow) or using an existing index (faster).

Benefits of Execution Plans:

By analyzing the plan, you can identify problems like:

Queries not using available indexes, leading to slow performance.

Missing indexes that could improve query speed.

How to Use Execution Plans:

Understanding execution plans can be complex and depends on the specific database platform you're using.

If you need help interpreting an execution plan, consult your database administrator (DBA) – they're the experts!

Summary:

Execution plans are like diagnostic tools that help you understand how your database executes queries. By analyzing them, you can identify and fix performance bottlenecks, making your queries run faster and smoother.

# Chapter Summary

* Databases: there are two main types: relational(structured data) and non-relational(flexible data).

* Database Design: transactional databases (OLTP) for daily operations use a normalized schema(strict structure). Analytical databases (OLAP) for analysis use a denormalized schema with star/snowflake schema designs for dimensional modeling (facts & dimensions).

* Data Acquisition: data can come from internal transactional systems (ETL/ELT) or external sources(APIs, web scraping, public databases) you can also conduct surveys or observations.

* Data Manipulation: SQL is the standard language for querying and manipulating data in relational databases (filtering, sorting, etc.).

* Performance Optimization: For large datasets, use parameterization (reduce parsing) and subsets/temporary tables to reduce data worked with. Use execution plans with DBAs to check for efficient indexing.

# chapter Review

**Describe characteristic of OLTP and OLAP systems.**

Two main categories of relational databases are transactional (OLTP) and analytical (OLAP). Transactional systems use highly normalized schema design, which allows for database reads and writes to perform well. 

Analytical systems are denormalized and commonly have a star or snowflake schema design. A star design simplifies queries by having a main fact table surrounded by dimensions. A snowflake is more normalized than a star. This approach reduces storage requirements, the queries are more complex than in a star schema.

**Describe the approaches for handling dimensionality**

It is important to keep track of how data changes over time to perform historical analysis. SQL queries to retrieve a value at a specific point in time are complex. a table design add start date and end date columns that allows for more straightforward queries. Enhancing the design with a current flag column makes analytical queries even easier to write.

**Understand integration and how to populate a data warehouse**

The more data an organization has, the more impactful the analysis it can conduct. The extract, transform, and load (ETL) process copies data from transactional to analytical databases. Suppose an organization wants to use the power of a relational database to reformat the data for analytical purposes. In that case, the order changes to extract, load, and transform. Regardless of the approach, remember that a delta load migrates only changed data.

**Differentiate between data collection methods.**

Data can come from a variety of sources. An organization may scrape websites or use publicly available databases to augment its data. While web scraping may be the only way to retrieve data, it is better if a published application programming interface exists. An API is more reliable since its structure makes for a consistent interface. If you want to capture the voice of the customer, a survey is a sound approach. Collecting data through observation is a great way to validate business processes and collect quantitative data.

**Describe how to manipulate data and optimize queries.**

Analytical databases store massive amounts of data. Manipulating the entire dataset for analysis is frequently infeasible. To efficiently analyze data, understand that SQL has the power to filter, sort, and aggregate data. When focusing on a particular subject, creating a subset is an ideal approach. Although it is possible to create permanent tables to house subsets, using a temporary table as part of a query is viable for ad hoc analysis. When an analytical query performs poorly, use its execution plan to understand the root cause. It is wise to work with a database administrator to understand the execution plan and ensure that indexes exist where they are needed.

*Chapter 4:* Data Quality

In this chapter, we will learn about:
  * Understanding the challenges of data quality

  * Identifying common reasons for cleansing and profiling datasets.

  * Executing data manipulation techniques.

  * Applying data quality control concepts.

**Data Quality Challenges**

In chapter 3, we discussed: Databases and data acquisition. We said that data warehouse aggregate multiple data sources and provide a platform for conducting analysis. Each data source has its own unique quality issues that need resolution before finding its way into a data warehouse. Whether performing an ETL process, into a new set of data warehouse tables, an analyst needs to examine each data source and resolve any underlying quality issues.

**Duplicate Data**

duplicate data occurs when data representing the same transaction is accidentally duplicated within a system. Humans are primarily responsible for creating the duplicate data. System architects work diligently to prevent duplicate data from being created. 

Best way to prevent duplicate data is to prevent its creation in the first place. One common approach to stopping duplicate data before it gets into a system is a visual warning to alert users. 

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/dcf00f44-1f12-4cc1-b619-0740916643af)

**Redundant Data**

This happens when the same data exists in multiple places within a system. Data redundancy is a function of integrating multiple systems.

Multiple aource systema that perform different business functions and use shared data elements create the conditions for data redundancy. When record changes in one system, there is no guarantee that its new value changes in another system. Since there is no certainty of data synchronization, a data element can have conflicting values across systems. When integrating multiple data sources, dealing with redundant data is a persistent challenge.

There are several ways for resolving redundant data. One approach synchronizes changes to shared data elements between Accounting and Sales systems. technical and political realities can make synchronizing source systems unfeasible.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/3f248cec-8f4e-400b-92aa-795e4b2fe8a0)


**Missing Values**

Another issues that impacts data quality is the concept of missing values. Missing values occur when you expect an attribute to contain data but nothing is there. Missing values are also known as null values. A null value is the absence of a value. A null is not a space, blank or other character.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/c5fb5948-798b-4ac1-bfaa-ae521eeb8177)

Null values present several challenges depending on the tools you use to analyze data. If you use the AVG function in SQL to find the numeric average of the data from Figure 4.7, you will get a number because the AVG function excludes null values.

To handle missing values, you first have to check for their existence. SQL offers functions to check for null and functions that can replace a null with a user-specified value.

**Invalid Data**

Invalid data are values outside the valid range for a given attribute. An invaid vlaue violates a business rule instead of having an incorrect data type. You have to understand the context of a system to determine whether or not a value is invalid.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/f0e999fd-7127-4133-aff5-e3374d60cd15)

Invalid values violate business rules, not technical rules. e.g. -99,999 is a valid value, but it is an invalid temperature for a location earth. 

Text data is more complex. One thing that leads to invalid character data is an absence of referential integrity within a database. If two tables have a relationship but no foreighn keys, the conditions for invalid character data exists. 

**Nonparametric Data**

- it is data collected from categorical variables. The categories indicate the differentation and sometimes they have a rank order associated with them.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/a686c535-9fbc-4f20-ac52-98f5a584bcd6)

**Data Outliers**

A dat outlier is a value that differs significantly from other observations in a dataset. With outliers, you need to understand wht they exist and whether they are valid in the context of your analysis. Outliers exist regardless of data type.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/5d685ce4-9e0f-461c-8cc7-4236acf6dc16)

**Specification Mismatch**

a specification describes the target value for a component. A specification mismatch occures when an individual component's characteristics are beyond the range of acceptable values.  it happens when something you have (a component, data) doesn't meet the requirements(specifications) for its use. When data is invalid, it has values that fall outside a given range. On the other hand, a specification mismatch occurs when data does not conform to its destination data type. 

**Data Type Validation**

- it ensure that values in a dataset have a consistent data type.

Data type validation ensures data in a dataset adheres to the data types defined in the database schema.
This helps maintain data integrity and prevents errors during analysis.
Common programming languages like SQL, Python, and R have functions to validate data types before loading.

***Data Manipulation Techniques***

**Recoding Data**

This is a technique you can use to map original values for a variable into new values to facilitate analysis. Recoding groups data into multiple categories, creating a categorical variable. A categorical variable is either nominal or ordinal. Nominal variables are any variable with two or more categories where there is no natural order of the categories, like hair color or eye color. Ordinal variables are categories with an inherent rank. Variable values fit into a fixed number of categories, similar to how lookup table work. Recoding is helpful when you have numeric data you want to analyze by category.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/14024eb1-75d5-4c23-833a-ee37a71c5ea2)

**Derived Variables**

- is a new variable resulting from a calculation on an existing variable.


**Data Merge**

uses common variable to combine multiple datasets with different structures into a single dataset. Merging data improves data quality by adding new variables to your existing data. Additional variables make for a richer dataset, which positively impacts the quality of your analysis. ETL processes commonly append data while transforming data for use in analytical environments.
Data merge adds a column to a dataset, merging gives you additional data about a specific observation.

Combines datasets with a common variable into a single dataset. It improves data quality by adding new variables, creates a richer dataset for better analysis.
It allows you to combine information from various sources, providing a more holistic view of your data subject.

**Data Blending**

- it combines multiple sources of data into a single dataset at the reporting layer.

Data blending combines data from multiple sources at the reporting layer (e.g. visualization tools). Done on-demand by analysts for specific needs. Blended data doesn't persist - exists only for the current analysis. Requires some understanding of how data maps across systems.

ETL process scheduled process managed by IT. It extracts data from source systems, transforms it and loads it into a data warehouse. Blended data persists in the data warehouse. 

The difference between the two:
  * timing - ETL is scheduled, data blending is ad hoc.

  * Persistence - ETL creates a permanent dataset, data blending is temporary.

  * User - ETL is IT-managed, data blending empowers analysts.

Both of them are valuable tools for data analysis. Understanding their strengths and differences helps you choose the right approach for your specific needs.

**Concatenation**

- it is the merging of separate variables into a single variable. It is highly effective technique when dealing with a source system that stores components of a single variable in multiple columns.

The need for concatenation frequently occurs when dealing with date and time. 
It is useful when generating address information. 

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/b302d845-f221-47fe-873d-a4e627c1d126)

**Data Append**

- it combines multiple data sources with the same structure, resulting in a new dataset containing all rows from the original datasets. When appending data, you save the result as a new dataset for ongoing analysis.
It creates a new dataset containing all rows from the originals. It increases data volume for analysis. Provides a more comprehensive view of a single subject.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/e3ce159d-baff-415c-9fd6-cd111f8075cb)

**Imputation**

- this is a technique for dealing with missing values by replacing them with substitutes. When merging mulitple data sources, you may end up with a dataset with many nulls in a given column. If you are collecting sensor data, it is possible to have missing values due to collection or transmission issues.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/ae854a6b-852b-44ad-921e-dc23afc437f0)

here are a few approaches an analyst can use for imputing values:

  - Remove Missing Data: you can remove rows with missing values without impacting the quality of your overall analysis.

  - Replace with Zero: you can replace missing values with a zero. Whether or not it is appropraite to replace missing data with a zero is contextual. Zero is not an appropraite value, as a person's weight should be a positive number.

  - Replace with Overall Average: instead of zero, you can compute the average Weight value for all rows that have data and then replace the missing Weight value with that calculated average.

  - Replace with Most Frequent (Mode):  Alternatively, you can take the most frequently occurring value, called the mode, and use that as the constant.

  - Closest Value Average:  With this approach, you use the values from the rows before and after the missing values. For example, to replace the missing measurements for 2/13/2021 and 2/14/2021, take the values from 2/12/2021 and 2/15/2021 to compute the average.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/48d6a714-ce81-400d-8ba2-a6f71eeeb59a)


**Reduction**

When dealing with big data, it is frequently unfeasible and inefficient to manipulate the entire dataset during analysis. *Reduction* is the process of shrinking an extensive dataset without negatively impacting its analytical value. 

There are a variety of reduction techniques from which you can choose. Selecting a method depends on the type of data you have and what you are trying to analyze. Dimensionality reduction and numerosity reduction are two techniques for data reduction.

**Dimensionality Reduction**

- it removes attributes from a dataset. Removing attributes reduces the dataset's overall size.

* Reduced Dataset Size: By removing irrelevant attributes, it makes your data more compact and easier to store and manipulate.

* Improved Processing Efficiency: algorithms perform better with lower-dimensional data. Dimensional reduction can streamline various machine learning tasks by reducing the computational cost of processing the data.

* Focus on revelant features: it helps you focus on the most informative features for your specific analysis. This can lead to better insights and more accurate models.

**Numerosity Reduction**

* Managing large data volumes: As datasets grow in size, analyzing every single data point can be impractical. It helps us summarize and represent the data efficiently, enabling better analysis.

* Summarization with Histograms: They provide a visual representation of how frequently values occur in your data, allowing you to identify patterns and trends without getting bogged down by individual data points.

* Histogram Efficiency: They offer a quick and informative way to understand the distribution of your data.

* Sampling efficiency: By selecting a representative subset of the data, you can gain valuable insights while significantly reducing processing time.

**Aggregation**

* Summarizing Raw Data: Data aggregation condenses large amounts of data into a more manageable and informative format. This makes it easier to identify patterns, trends and relationships within the data.

* Benefits of summarization: it provides summaries that can answer specific questions and facilitate better decision-making.

* Real-World Analogy: Distance to Empty:  The road trip analogy is a great way to explain data aggregation in a relatable context.  The car's computer aggregates various sensor readings to provide a crucial metric - distance to empty.  This summarized information allows you to make informed decisions about refueling and avoid being stranded.

* Balancing Privacy and Insights:  Data aggregation can also be used to protect privacy.  In your payroll example,  aggregating data to calculate average compensation protects the CEO's individual salary while still providing insights into overall employee compensation structure.

Overall, data aggregation is a powerful tool for extracting knowledge from data. By condensing large datasets into meaningful summaries, it allows us to gain valuable insights, make data-driven decisions, and even protect sensitive information.

**Transposition**

* Restructuring for Analysis:  Data transposition involves changing the layout of data from rows to columns or vice versa. This can be beneficial for certain analyses where the data needs to be presented in a different orientation for better understanding.

* Example: Sales Data Analysis:  The sales data example clearly demonstrates the value of transposition.  By transposing the data, you can easily calculate total sales per salesperson by fiscal year, which would be cumbersome in the original format.

* Improved Readability:  As you mentioned, transposed data can be much easier to read and analyze, especially for datasets with many rows.  This is because you can focus on a particular salesperson's performance across different fiscal years without having to scroll through numerous rows.

* Combining with Aggregation:  The most powerful aspect of transposition is when it's combined with data aggregation.  This allows you to not only rearrange the data but also summarize it for deeper insights.  The final table you presented (Figure 4.31) is a perfect example.  It combines sales data by salesperson and fiscal year, making it easy to identify top performers and trends over time.

In conclusion, data transposition is a valuable technique for transforming data into a format that facilitates analysis and  discovery of insights.  By strategically using transposition and combining it with aggregation, you can make data more readable, informative, and suitable for data visualization tasks covered in later chapters.

**Normalization**

* Scaling for Comparison: Data normalization in this context refers to scaling data from different units to a common range. This allows you to compare features that were previously measured in different units.

* Importance of Consistent Units: As you mentioned in the athlete data example (Figure 4.32), it's challenging to compare heights in inches with weights in pounds. Their different scales make direct comparison misleading.

* Normalization Techniques: There are various data normalization techniques, like min-max scaling (used in Figure 4.33) that establish a common range (often 0 to 1) for all features. This ensures all features contribute equally to statistical analysis.

* Statistical Analysis Benefits: By normalizing the data, you prepare it for statistical analysis techniques like correlation analysis, which wouldn't be meaningful with features on different scales.

In essence, data normalization bridges the gap between features measured in different units, enabling a more holistic and meaningful analysis of your data.

**Min-Max Normalization**

* Identify Minimum and Maximum Values: As you mentioned, the first step is to find the minimum and maximum values within the feature you want to normalize (e.g., Height in this case). In Figure 4.32, the minimum height is 68 inches and the maximum is 76 inches.

* Apply the Formula: The min-max normalization formula is:

Normalized Value = (Value - Min) / (Max - Min)
For Athlete ID 1 with a height of 71 inches, the normalized value would be:

Normalized Value = (71 inches - 68 inches) / (76 inches - 68 inches) = 0.4285
This translates the height of 71 inches (originally measured in inches) to a value between 0 and 1, representing its relative position within the range of all heights in the data.

* Repeat for All Values: The normalization process is repeated for each data point in the feature you're scaling.
While min-max normalization is straightforward, it's important to be aware of its limitations.  For instance, it can be sensitive to outliers that can significantly affect the minimum or maximum values used for scaling.

**Parsing/String Manipulation**

* Composite Data Issues:  A composite data issue arises when a single column contains data points that represent multiple attributes combined into one string. This can hinder analysis because each data point isn't atomic (indivisible).

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/2fb14e2a-ce4d-4fa8-ab36-180981bf6865)


* Splitting Composite Columns:  As in Figure 4.34, string parsing techniques can be used to break down composite columns into separate columns, each representing a distinct attribute. This improves data organization and facilitates analysis.

* Distributed Data Issues:  Distributed data occurs when data that logically belongs together is spread across multiple columns. This can make analysis cumbersome.

![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/2af3b630-9855-4ac5-8e2b-8bbcd97a7589)


* Combining Distributed Columns:  String concatenation (Figure 4.35) is a technique for combining separate columns into a single column when the data points are related. This can simplify analysis.

* String Manipulation for Quality:  String manipulation techniques can also be used to improve data quality.  For instance, Figure 4.36 demonstrates how to address inconsistencies in state abbreviations.

  ![image](https://github.com/MisterWest11/Data_Analytics-Week-1---2/assets/152319557/fdc19010-b6a1-487b-ad9c-cfc196700a40)


In conclusion, data manipulation plays a crucial role in dealing with composite and distributed data structures, as well as improving data quality through string manipulation techniques. These actions ensure that your data is well-organized, consistent, and ready for meaningful analysis.

*Chapter 5:* Data Analytics and Statistics
