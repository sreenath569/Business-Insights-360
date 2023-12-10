# Business-Insights-360
This PowerBI project has been successfully executed through a collaborative effort with the CodeBasics Team during the Data Analytics Bootcamp.

[CodeBasics](https://codebasics.io/#ourcourses)

## AtliQ Hardware(Client Company)
AtliQ Hardware is a Company that sells hardware like Accessories, Desktop, Networking, Notebook, Peripherals & Storage devices to different customers.

Accessories includes Batteries, Keyboard, Mouse etc.

Desktop includes Business Laptop, Personal Desktop etc.

Networking includes Wifi extender.

Notebook includes Business Laptop, Gaming Laptop, Personal Laptop etc.

Peripherals includes Graphic Card, Internal HDD, MotherBoard, Processors etc.

Storage Devices includes External SDDs, USB Flash Drives etc.

[AtliQ Customers](https://github.com/sreenath569/Business-Insights-360/blob/main/DATASET/Images/AtliQ%20Customers.jpeg)

## Problem Statement
AtliQ Hardware, a leading provider of diverse hardware solutions, faces the challenge of efficiently managing and analyzing its extensive product inventory and sales data. The company sells a wide range of hardware, including Accessories , Desktops , Networking equipment , Notebooks , Peripherals and Storage Devices.

## Solution
To enhance decision-making processes and gain valuable insights, Product Owner of AtliQ Hardware aims to leverage PowerBI for developing a comprehensive business intelligence solution.

[dashboard views](https://github.com/sreenath569/Business-Insights-360/blob/main/DATASET/Images/dashboard%20views.jpeg)

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
   
   [dim_customer](https://github.com/sreenath569/Business-Insights-360/blob/main/DATASET/DB%20Files/dim_customer.jpeg)
   
   [dim_market](https://github.com/sreenath569/Business-Insights-360/blob/main/DATASET/DB%20Files/dim_market.jpeg)
   
   [dim_product](https://github.com/sreenath569/Business-Insights-360/blob/main/DATASET/DB%20Files/dim_product.jpeg)

   [dim_date]()
       
Fact Tables
   
   [fact_sales_monthly](https://github.com/sreenath569/Business-Insights-360/blob/main/DATASET/DB%20Files/fact_sales_monthly.jpeg)
   
   [fact_forecast_monthly](https://github.com/sreenath569/Business-Insights-360/blob/main/DATASET/DB%20Files/fact_forecast_monthly.jpeg)
       
Supporting Facts
   
   [gross_price](https://github.com/sreenath569/Business-Insights-360/blob/main/DATASET/DB%20Files/gross_price.jpeg)
   
   [pre_invoice_deductions](https://github.com/sreenath569/Business-Insights-360/blob/main/DATASET/DB%20Files/pre_invoice_deductions.jpeg)
   
   [post_invoice_deductions](https://github.com/sreenath569/Business-Insights-360/blob/main/DATASET/DB%20Files/post_invoice_deductions.jpeg)
   
   [manufacturing_cost](https://github.com/sreenath569/Business-Insights-360/blob/main/DATASET/DB%20Files/manufacturing_cost.jpeg)
   
   [freight_cost](https://github.com/sreenath569/Business-Insights-360/blob/main/DATASET/DB%20Files/freight_cost.jpeg)   


    
### Data Tranformation( Power Query )

   Queries prepared:-

      LastSalesDate - get last sales date by referencing fact_sales_monthly
                     {List.Max(#"fact_sales_monthly"[date])}
      
      RemainingForecast - remaining forecast from last sales date by referencing fact_forecast_monthly
                           {Table.SelectRows(Source, each([date]>LastSalesDate))}

      fact_actuals_estimates - appending fact_sales_monthly & RemainingForecast

   Custom columns added in fact_actuals_estimates:-

      fisacl_year - Date.Year(Date.AddMonths([date],4)){AtliQ Hardware fiscal year Sept-Aug}

      gross_sales_amount - by merging fact_actuals_estimates & gross_price

      pre_invoice_discount_amount - by merging fact_actuals_estimates & pre_invoice_deductions

      net_invoice_sales_amount = [gross_sales_amount]-[pre_invoice_discount_amount]

   Best practices used in Power Query:-

      i. Naming the Query steps.
      ii. Write comments for Complex Transformations.
      ii. Grouping Tables.
      iii. Disable load for Tables that will not be used outside Power Query.
      iv. Keep the table names minimal.
      v. Query folding.

### Data Modeling & DAX Calculated Columns( Power BI )

   Data Modeling :-

      Established relationships between the tables by refering primary keys and foreign keys.
      
   DAX Calculated Columns in fact_actuals_estimates:-

      post_invoice_deductions_amount
      
      post_invoice_other_deductions_amount
      
      Net_sales_amount = Net_invoice_sales_amount - post_invoice_deductions_amount - post_invoice_other_deductions_amount
      
      manufacturing_cost
      
      freight_cost
      
      freight_other_cost
      
      total_cogs_amount = manufacturing_cost + freight_cost + freight_other_cost {cogs - cost of goods sold}
      
      gross_margin_amount = Net_sales_amount - total_cogs_amount
      
### Finance View

### Sales View

### Marketing View

### Supply Chain View

### Executive View

