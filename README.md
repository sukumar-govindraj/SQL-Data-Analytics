# SQL Analytics Project

Welcome to the **SQL Analytics** project! This repository contains SQL scripts and views that showcase best practices for data analysis in a data warehouse environment. From running totals to year-over-year comparisons, you’ll find a collection of scripts that demonstrate typical business intelligence patterns.

---

## Table of Contents

1. [Overview](#overview)  
2. [Project Structure](#project-structure)  
3. [Key Analyses](#key-analyses)  
   - [Cumulative Analysis](#cumulative-analysis)  
   - [Performance Analysis (Year-over-Year)](#performance-analysis-year-over-year)  
   - [Data Segmentation Analysis](#data-segmentation-analysis)  
   - [Part-to-Whole Analysis](#part-to-whole-analysis)  
   - [Customer Report](#customer-report)  
   - [Product Report](#product-report)  
4. [Database & Environment Notes](#database--environment-notes)  
5. [Setup and Usage](#setup-and-usage)  
6. [Contributing](#contributing)  
7. [License](#license)

---

## Overview

This project demonstrates practical examples of analytical SQL queries often used in business intelligence and data warehousing:

- **Cumulative & Running Totals**: Gain insights into progressive metrics (e.g., cumulative sales).  
- **Period-over-Period Comparisons**: Compare performance metrics between different time periods (e.g., year-over-year).  
- **Data Segmentation**: Categorize customers and products into tiers or segments based on specific business rules.  
- **Part-to-Whole Analysis**: See how much each category or segment contributes to a total.  
- **Consolidated Reporting**: Build comprehensive, single-view reports for customers and products.

Whether you’re a data analyst, BI developer, or just exploring SQL’s analytical capabilities, these scripts can serve as a blueprint or learning resource.

---

```plaintext
sql-analytics/
├── 1_Cumulative_Analysis.sql
├── 2_Performance_Analysis.sql
├── 3_Data_Segmentation.sql
├── 4_Part_To_Whole_Analysis.sql
├── 5_Customer_Report.sql
├── 6_Product_Report.sql
└── README.md         <-- You are here
```


- Each `.sql` file focuses on a distinct analytical theme.  
- The scripts can be run independently, though they assume some common table structures (fact tables, dimension tables) in a `gold` schema.

---

## Key Analyses

### Cumulative Analysis
- **Purpose**:  
  Calculate running totals or moving averages for metrics (e.g., total sales).  
- **Highlights**:  
  - Uses window functions (`SUM() OVER(...)`, `AVG() OVER(...)`).  
  - Simple example: Running total of year-to-date sales or moving average of prices.

### Performance Analysis (Year-over-Year)
- **Purpose**:  
  Assess how products perform against their historical data and their own average.  
- **Highlights**:  
  - Uses `LAG()` for period-over-period comparisons.  
  - Identifies trends: “Above Avg” / “Below Avg” sales, “Increase” / “Decrease” vs. last year.

### Data Segmentation Analysis
- **Purpose**:  
  Classify products or customers into categories (e.g., cost ranges, VIP vs. Regular).  
- **Highlights**:  
  - Leverages `CASE` statements and `GROUP BY` to create meaningful segments.  
  - Helps uncover patterns like which customers spend the most or how many products fall below certain cost thresholds.

### Part-to-Whole Analysis
- **Purpose**:  
  Determine how much each category contributes to overall metrics (e.g., total sales).  
- **Highlights**:  
  - Uses `SUM(...) OVER()` to compute total sales across all categories.  
  - Ideal for identifying top categories or tracking market share.

### Customer Report
- **Purpose**:  
  Combine key metrics about customers into a single view.  
- **Highlights**:  
  - Shows total orders, total sales, order frequency, average order value, and recency.  
  - Applies segmentation logic: “VIP,” “Regular,” or “New” based on spending and engagement.

### Product Report
- **Purpose**:  
  Combine product metrics into a single view for easy analysis.  
- **Highlights**:  
  - Shows total revenue, order count, customer count, average selling price.  
  - Segments products by total sales (High-Performer, Mid-Range, Low-Performer).

---

## Database & Environment Notes

1. **SQL Dialect**  
   - The scripts use a combination of T-SQL (Microsoft SQL Server) syntax and some window function features common in Postgres/Snowflake.  
   - If you encounter errors (e.g., `DATETRUNC` not recognized), adapt the functions (`DATEADD`, `DATEDIFF`, or your database’s equivalents).

2. **Schema & Tables**  
   - Assumes tables in a `gold` schema: `gold.fact_sales`, `gold.dim_products`, `gold.dim_customers`.  
   - Modify the scripts if your database uses different schema or table names.

3. **View Creation**  
   - Some scripts create views like `gold.report_customers` or `gold.report_products`.  
   - Adjust these names if you want to place them in a different schema or name convention.

---

## Setup and Usage

1. **Clone the Repository**  
   ```bash
   git clone https://github.com/sukumar-govindraj/SQL-Data-Analytics.git
   cd sql-analytics

