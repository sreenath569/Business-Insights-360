# Business-Insights-360
This PowerBI project has been successfully executed through a collaborative effort with the CodeBasics Team during the Data Analytics Bootcamp.

[CodeBasics](https://codebasics.io/#ourcourses)
[dim_customer](https://github.com/sreenath569/Business-Insights-360/blob/main/DATASET/Images/acquisition.png)
## AtliQ Hardware(Client Company)
AtliQ Hardware is a Company that sells hardware like Accessories, Desktop, Networking, Notebook, Peripherals & Storage devices to different customers.

Accessories includes Batteries, Keyboard, Mouse etc.

Desktop includes Business Laptop, Personal Desktop etc.

Networking includes Wifi extender.

Notebook includes Business Laptop, Gaming Laptop, Personal Laptop etc.

Peripherals includes Graphic Card, Internal HDD, MotherBoard, Processors etc.

Storage Devices includes External SDDs, USB Flash Drives etc.

![AtliQ Customers](https://github.com/sreenath569/Business-Insights-360/assets/70423931/c7f4617b-005b-41c5-a38a-9d5e7bc74b20)

## Problem Statement
AtliQ Hardware, a leading provider of diverse hardware solutions, faces the challenge of efficiently managing and analyzing its extensive product inventory and sales data. The company sells a wide range of hardware, including Accessories , Desktops , Networking equipment , Notebooks , Peripherals and Storage Devices.

## Solution
To enhance decision-making processes and gain valuable insights, Product Owner of AtliQ Hardware aims to leverage PowerBI for developing a comprehensive business intelligence solution.
![dashboard views](https://github.com/sreenath569/Business-Insights-360/assets/70423931/c128f32e-9bd0-49b5-b5bb-01dd86839022)

## Steps involved in this Project
### Data Collection
    **Data Sources**:-
    The Data Engineer at AtliQ Hardware has facilitated the data transfer in two distinct formats:
        i. Databases provided as SQL Text files (.sql files).
        ii. Excel files containing relevant data.


    **Local Database Setup**:-
    A local MySQL Database has been set up to efficiently manage and store the data.
    The provided SQL Text files have been imported into our local MySQL Database for centralized data storage and management.


    **Data Integration with PowerBI**:-
    The data residing in both the local MySQL Database and Excel files has been seamlessly imported into PowerBI.
    This integration serves as a crucial step in aggregating and visualizing the data for comprehensive analysis.


    **Establishment of Relationships**:-
    Post data loading into Power BI, careful consideration has been given to establishing relationships between the various tables.
    These relationships are essential for ensuring data consistency and accuracy throughout the analytical process.


    **Dimensional Date Table Creation**:-
    Within the Power Query Editor of Power BI, a Dimensional Date table has been created.
    This specialized table is pivotal for organizing and categorizing dates, providing a structured foundation for time-based analysis.


    **Benchmark Validation**:-
    The Benchmark numbers provided by the Business have been meticulously validated against the loaded data.
    This validation process ensures that the data aligns with the expected benchmarks and meets the predefined criteria.


    Tables/Queries Collected:-

    Dimension Tables
       [dim_customer](https://github.com/sreenath569/Business-Insights-360/blob/main/DATASET/Images/acquisition.png)
       dim_market
       dim_product
       
    Fact Tables
       fact_sales_monthly
       fact_forecast_monthly
       
    Others
       gross_price
       pre_invoice_deductions
       post_invoice_deductions
       manufacturing_cost
       freight_cost   
    
### Data Tranformation


