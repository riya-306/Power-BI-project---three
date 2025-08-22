Power BI Report Transition: SQL Server to MySQL

## Project Overview

This project focuses on creating a Power BI dashboard using data initially sourced from Microsoft SQL Server and later transitioning it seamlessly to MySQL. The end goal was to ensure smooth data integration, robust visualizations, and cross-database adaptability while maintaining consistency in measures, relationships, and visuals.

## Problem Statement

Organizations often migrate their databases from one platform to another (e.g., SQL Server → MySQL) due to scalability, cost, or system requirements. This transition poses challenges, such as different SQL syntaxes, schema alignment, and ensuring that existing BI reports remain functional without rebuilding from scratch.


## Key Goals-


1)Design and develop an interactive Power BI report with structured visuals.

2)Create calculated columns, measures, and data transformations to enable deeper insights.

3)Implement slicers and filters for user-friendly exploration.

4)Transition the report’s data source from Microsoft SQL Server to MySQL while keeping all visuals and measures intact.

5)Demonstrate adaptability to cross-database environments.


## Steps Followed-


- Step 1 : **Defining Data Sources & Real-Time Scenarios-**
 After creating new database.In this step, we outlined the data sources for the project—Microsoft SQL Server and MySQL Workbench. The focus was on simulating real-world situations such as:

1)-Shifting Power BI reports from test environment to production environment.

2)-Migrating reports from SQL Server to MySQL when an organization changes its primary data source.

These scenarios highlight the importance of ensuring report accuracy, consistency of KPIs, and adaptability across different data platforms.

- Step 2 : Dataset Structure & KPI Requirements

Here, we explored the project dataset, which included:

1)-Demand-Availability Table: Order Date, Product ID, Availability, and Demand.

2)-Products Table: Product ID, Product Name, and Unit Price.

From these tables, we derived business KPIs to be represented in Power BI:

Page 1: Average Demand per Day, Average Availability per Day, Total Supply Shortage.

Page 2: Total Loss, Total Profit, Average Daily Loss.

This step ensures the dataset is well-understood and mapped to the reporting requirements before building the Power BI dashboards.

- Step 3 :**Importing Data into SQL Server (Test Environment)-**

In this step, the dataset was imported into SQL Server Management Studio (SSMS) to simulate a real-world test environment. The process included:

A)-Creating a new database named Test_Env.

B)-Using the Import Flat File option to load two datasets:

-Inventory Dataset (Order Date, Product ID, Availability, Demand).

-Products Table (Product ID, Product Name, Unit Price).

C)-Verifying successful import by running SQL queries (SELECT * FROM …) to confirm data availability.

The test environment now contains both inventory and product details, enabling us to build Power BI reports. A similar process can be followed for the production environment later.





- Step 4 :**SQL Data Integration-**

We explored the Products and Inventory tables in SQL Server, checked data quality, and performed a LEFT JOIN on ProductID to merge them. A new consolidated table was created using SELECT INTO, combining order details, product info, availability, demand, and pricing—ready for import into Power BI.

<img width="979" height="403" alt="image" src="https://github.com/user-attachments/assets/d4aea4e2-c34c-4532-9a34-ff2d670314f2" />


- Step 5 :**Power BI Data Connection & Report Setup-**

We connected Power BI to SQL Server (Test Environment), loaded the consolidated table, and refined data types in Power Query. Background templates (created in Canva) were applied to design report pages with clean layouts. Page 1 was structured for KPIs like average demand, average availability, and total supply storage, while Page 2 focused on financial KPIs such as total profit, total loss, and average daily loss. The report was saved as Prod Power BI Report for future use with production data.




- Step 6 :**KPI Creation using DAX-**

We created a dedicated Measures Table in Power BI and built DAX measures for key KPIs:

--Average Demand per Day = Total Demand ÷ Total number of Days

--Average Availability per Day = Total Availability ÷ Total number of Days

--Total Supply Shortage = Total Demand – Total Availability

These KPIs were displayed using card visuals and formatted for clarity. Filters (by Product and Date) were added to allow dynamic KPI insights, with the filters pane styled for better user experience

example of 1 measure - <img width="979" height="33" alt="image" src="https://github.com/user-attachments/assets/02a78a10-25d6-4c62-8843-6900d70dbce3" />



- Step 7 :**KPI Calculation & Report Page 2-**

We created a second report page to display KPIs using DAX measures. A custom Profit/Loss column was built by subtracting demand from availability. Using this, we defined:

Total Profit → positive values × unit price

Total Loss → negative values × unit price

Average Daily Loss → Total Loss ÷ Total number of Days

These measures were visualized with card visuals for clear representation. Filters for Product and Order Date were added, and the filters pane was styled for consistency (black background, white text). The second page now provides a clean, interactive KPI dashboard aligned with Page 1.

snap of a complete measure table - <img width="264" height="382" alt="image" src="https://github.com/user-attachments/assets/fbd55e7b-9a52-4e46-83fe-032c3b201c9c" />

 
- Step 8 :**Adjusting KPI Measures-**

To make the KPI values clearer, the measures for Total Loss and Average Daily Loss were modified by multiplying them with -1. This ensured that the results appear as positive values since the word "loss" is already included in the labels.

- Step 9 :**Setting Up Production Environment**-

A new production database (Prod) was created in SQL Server, and the Production Inventory Dataset (1043 records) along with the Products Table were successfully imported. The data was verified using SQL queries, showing the difference between test and production environments. Moving forward, the report will be shifted from test to production by updating data source settings instead of rebuilding it.

- Step 10 : Shifting Reports to Production
Reports created in the test environment were moved to the production database by updating data source settings in Power BI. This ensured that the reports reflected the complete production dataset while preserving the visuals, measures, and interactivity built during testing.

- Step 11 :**Importing Data into MySQL-**
In this step, we created a new production database in MySQL Workbench and imported the production inventory and products tables using the Data Import Wizard. We then modified and executed update statements (taken from SQL Server) by adjusting column names and table references, after disabling safe update mode. With the updates applied successfully, the production data was ready in MySQL for connecting Power BI and migrating reports from SQL Server.


- Step 12 :**Creating a New Table in MySQL for Report Transition-**
In this step, we created a new table named New_Table in MySQL Workbench to match the structure of the one previously built in SQL Server. The column names were aligned with SQL Server to ensure compatibility with existing DAX measures and avoid breaking calculations. Since SQL syntax differs between SQL Server and MySQL, adjustments were made while writing the query, including proper joins, aliases, and column renaming. Once executed, the new table was successfully created with all records loaded, preparing the data for transitioning the Power BI report from SQL Server to MySQL as the new data source.

- Step 13 :**Connecting Power BI with MySQL Database-**

In this step, we established a connection between Power BI Desktop and the MySQL database. Using the Get Data option, we selected MySQL Database, entered the server as localhost, and specified the database prod along with a query to fetch data from New_Table. After providing the root username and password, the data was successfully loaded into Power BI. The imported table appeared in the model view, alongside existing tables from SQL Server, confirming that the MySQL data source was now integrated and ready for use in the report transition process.


# Snapshot of Dashboard 1 -

<img width="923" height="516" alt="image" src="https://github.com/user-attachments/assets/c5e947ea-45f6-4a09-acaa-feb4be5f9aca" />


# Snapshot of Dashboard 2 - 

<img width="929" height="519" alt="image" src="https://github.com/user-attachments/assets/40a35865-7263-4a68-91be-97f4423fe701" />

# Key Learnings

1) Handling SQL syntax differences between SQL Server and MySQL.

2) Best practices for aligning schemas during database transitions.

3) Designing BI dashboards that remain consistent even when the backend data source changes.
