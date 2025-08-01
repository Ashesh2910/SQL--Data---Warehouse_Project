# SQL-Data-Warehouse_Project
👋 Welcome to the Modern Data Warehouse Project!

This project demonstrates a scalable data warehouse built with SQL Server, following the Medallion Architecture (Bronze, Silver, Gold). It features clean ETL pipelines, optimized data models (fact & dimension tables), and SQL-based analytics for reporting and insights.

Explore the code, learn the structure, and feel free to contribute. Let’s turn data into decisions! 🚀


## 🏗️ Data Architecture

The data architecture for this project follows Medallion Architecture **Bronze**, **Silver**, and **Gold** layers:
![Data Architecture](https://github.com/Ashesh2910/SQL--Data---Warehouse_Project/blob/main/docs/Data_architecture.png)
1. **Bronze Layer**: Stores raw data as-is from the source systems. Data is ingested from CSV Files into SQL Server Database.
2. **Silver Layer**: This layer includes data cleansing, standardization, and normalization processes to prepare data for analysis.
3. **Gold Layer**: Houses business-ready data modeled into a star schema required for reporting and analytics.


## 📖 Project Overview

This project involves:

1. **Data Architecture**: Designing a Modern Data Warehouse Using Medallion Architecture **Bronze**, **Silver**, and **Gold** layers.
2. **ETL Pipelines**: Extracting, transforming, and loading data from source systems into the warehouse.(https://github.com/Ashesh2910/SQL--Data---Warehouse_Project/blob/main/docs/ETL%20FLOW.png)
3. **Data Modeling**: Developing fact and dimension tables optimized for analytical queries.(https://github.com/Ashesh2910/SQL--Data---Warehouse_Project/blob/main/docs/Data%20Model.png)
4. **Analytics & Reporting**: Creating SQL-based reports and dashboards for actionable insights.


## 🚀 Project Requirements

### Building the Data Warehouse (Data Engineering)

#### Objective
Develop a modern data warehouse using SQL Server to consolidate sales data, enabling analytical reporting and informed decision-making.

#### Specifications
- **Data Sources**: Import data from two source systems (ERP and CRM) provided as CSV files.
- **Data Quality**: Cleanse and resolve data quality issues prior to analysis.
- **Integration**: Combine both sources into a single, user-friendly data model designed for analytical queries.
- **Scope**: Focus on the latest dataset only; historization of data is not required.
- **Documentation**: Provide clear documentation of the data model to support both business stakeholders and analytics teams.

---
## 📊 EDA & Advanced Data Analytics Project Using SQL

This project showcases a complete Exploratory Data Analysis (EDA) and Advanced Analytical Framework using SQL on a star-schema structured dataset. The goal is to uncover insights, detect patterns, and answer key business questions through well-structured SQL queries, from data exploration to performance benchmarking.

--------

## 🔍 Project Objectives

1. 🗂 Database & Dimension Exploration
      - Understand the database structure, table relationships, and metadata.
      - Explore dimension tables such as customers, products, and categories.
    
2. 📅 Date Range Analysis
      - Identify the temporal scope of the dataset.
      - Analyze customer age and order activity over time.
  
3. 📈 Key Metrics & Aggregation
      - Generate high-level KPIs: total sales, average price, customer/order counts.
      -  Consolidated metrics dashboard using SQL aggregations and UNION ALL.
    
4. 📊 Magnitude Analysis
     - Break down metrics by categories, countries, and customer segments.
     - Assess data distribution and value concentration across dimensions.

5. 🏆 Ranking Analysis
    - Rank products and customers by revenue, orders, and activity.
    - Use ROW_NUMBER(), RANK(), and DENSE_RANK() for dynamic rankings.


## 📈 Advanced Analytical Layers

 6. ⏱ Change Over Time Analysis
    - Track growth, trends, and seasonal behaviors in sales and orders.
    - Time-series analytics with LAG() and time-window logic.

7. ➕ Cumulative & Moving Averages
    - Use SUM() OVER() and AVG() OVER() to calculate running totals.
    - Identify long-term trends and growth consistency.

8. 📆 Year-over-Year / Month-over-Month Performance
    - Evaluate business growth compared to previous periods.
    - Analyze improvements, declines, and benchmark KPIs.

9. 🧩 Data Segmentation
    - Segment customers, products, and regions for focused insights.
    - Build custom segment logic using CASE and grouping.

10. 🧮 Part-to-Whole Comparisons
    - Understand the contribution of each segment to overall performance.
    - Useful for market share, A/B testing, and category comparisons.

---------

## 🛠 Tools & Techniques Used
SQL Platform: Microsoft SQL Server

## Techniques:

- Basic & complex queries, joins, subqueries, CTEs
- Aggregations: SUM(), AVG(), COUNT()
- Window Functions: ROW_NUMBER(), RANK(), DENSE_RANK(), LAG()
- Window Functions: SUM() OVER(), AVG() OVER()
- Cumulative Metrics: SUM() OVER(), AVG() OVER()
- Conditional Logic: CASE WHEN
- Grouping & ordering for segmentation and ranking

--------


## 🧾 Customer Analytics Report
In addition to EDA and advanced analytics, this project includes a Customer Report that consolidates detailed insights about customer behavior, segmentation, and performance metrics.

📌 Report Purpose
To provide a 360° view of each customer, enabling data-driven decisions related to marketing, customer retention, and sales strategies.

📊 Report Highlights

      
      - Captures customer names, birthdates, and transaction histories.
      - Calculates age and classifies customers into age groups.
      - Customer Segmentation
        
      - Customers are segmented into:
            - 🏅 VIP: High purchase frequency and total spend
            - 🔁 Regular: Consistent but average engagement
            - 🆕 New: Recently acquired, limited transaction history
        
      - Aggregated Metrics
            - Total Orders
            - Total Sales
            - Total Quantity Purchased
            - Distinct Products Purchased
            - Customer Lifespan (in months)
        
      - Key KPIs
            - Recency: Time (in months) since last purchase
            - Average Order Value (AOV)
            - Average Monthly Spend

------------------

## 📂 Repository Structure
```
data-warehouse-project/
│
├── datasets/                           # Raw datasets used for the project (ERP and CRM data)
│
├── docs/                               # Project documentation and architecture details
│   ├── etl.drawio                      # Draw.io file shows all different techniquies and methods of ETL
│   ├── data_architecture.drawio        # Draw.io file shows the project's architecture
│   ├── data_catalog.md                 # Catalog of datasets, including field descriptions and metadata
│   ├── data_flow.drawio                # Draw.io file for the data flow diagram
│   ├── data_models.drawio              # Draw.io file for data models (star schema)
│   ├── naming-conventions.md           # Consistent naming guidelines for tables, columns, and files
│
├── scripts/                            # SQL scripts for ETL and transformations
│   ├── bronze/                         # Scripts for extracting and loading raw data
│   ├── silver/                         # Scripts for cleaning and transforming data
│   ├── gold/                           # Scripts for creating analytical models
│
├── tests/                              # Test scripts and quality files
│
├── README.md                           # Project overview and instructions
├── LICENSE                             # License information for the repository
├── .gitignore                          # Files and directories to be ignored by Git
└── requirements.txt                    # Dependencies and requirements for the project
```
---
