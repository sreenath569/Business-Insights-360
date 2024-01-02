# Business Insights 360 - AtilQ Hardware
This PowerBI project has been successfully executed through a collaborative effort with the CodeBasics Team during the Data Analytics Bootcamp.

Data Analytics Bootcamp link - [CodeBasics](https://codebasics.io/#ourcourses)

## AtliQ Hardware(Client Company)
AtliQ Hardware is a Company that sells hardware like Accessories, Desktop, Networking, Notebook, Peripherals & Storage devices to different customers.

      Accessories includes Batteries, Keyboard, Mouse etc.
      Desktop includes Business Laptop, Personal Desktop etc.
      Networking includes Wifi extender.
      Notebook includes Business Laptop, Gaming Laptop, Personal Laptop etc.
      Peripherals includes Graphic Card, Internal HDD, MotherBoard, Processors etc.
      Storage Devices includes External SDDs, USB Flash Drives etc.

## Overview
AtliQ Hardware, a leading provider of diverse hardware solutions, faces the challenge of efficiently managing and analyzing its extensive product inventory, sales and finance data. To overcome the challenges, the Product Owner of AtliQ Hardware decided to develop a comprehensive business intelligence solution with the help of CodeBasics team.  

This initiative aims to comprehensively address stakeholder inquiries across finance, sales, marketing, and supply chain domains. By providing thorough insights and analysis, the project seeks to enhance decision-making processes and foster strategic alignment within the organization. Ultimately, its goal is to optimize performance and drive sustainable success across multifaceted business aspects.

## Project Workflow
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
    
    Tables:-
      dim_customer(dimension)
      dim_market(dimension)
      dim_product(dimension)
      fact_sales_monthly(fact)
      fact_forecast_monthly(fact)
      gross_price(supporting fact)
      pre_invoice_deductions(supporting fact)
      post_invoice_deductions(supporting fact)
      manufacturing_cost(supporting fact)
      freight_cost(supporting fact)
      NsGmTarget(supporting fact)


    
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
      
### Key Learnings

