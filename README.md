# Operating Room (OR) Efficiency & Financial Analytics
An end-to-end Power BI and SQL analysis project focusing on healthcare operations, data cleaning, and key performance indicator (KPI) tracking within a hospital's operating room database.
This project cleans operational healthcare data and analyzes -Operating Room turnaround times-, evaluate Turnaround Time (TAT), staffing levels, using a **25 minute benchmark**. Evaluates operational efficiency, and quantifies the financial impact of scheduling delays.
Built Power BI dashboards tracking how Staffing numbers' change affect TAT, leading to costly clinical overtime. I used SQL to prove and validate, the Power BI results. My analysis helped manage these overtime expenses.


📂 Repository Structure
   -`README.md` — Project documentation and executive summary (this file).
   -`📁 SQL_Scripts/` —`OR_SQL_cleaning_&_analysis.sql`: Complete script containing data cleaning updates and analytical queries.
   -`📁 PowerBI_Report/` — Contains the interactive `.pbix` Power BI file.
   -`📁 Assets/` — High-resolution screenshots of dashboards and data models.

 Tech Stack
   Database Management System:** MySQL / Local RDBMS
   
 Data Source
    Source: Kaggle 
    Dataset Description: Contains [e.g., 9217 rows  from 2023 to 2024].
    Key Attributes:Patient Id,	Patient Admission Date,	Patient First Inital,	Patient Last Name, Patient Gender,	Patient Age,	Patient Race,	    Department Referral,	Turnover staffing number,	OR turnover  time,	ICU recovery. 

 ETL & Data Cleaning
    Date Standardizing: Converted the Patient Admission Date column from a string/text format with slashes (/) into a proper  DATETIME type.
    Encoding Fix: Renamed the column ï»¿Patient Id (a typical artifact caused by a UTF-8 BOM signature) to a clean Patient Id.
    Handling Missing Values: Replaced NULL values and blank strings ('') with 0 in the Turnover staffing number column to prevent skewed   
    averages.
    Dropping Redundant Data: Removed the unnecessary column ICU recovery
  
  Data Modeling
     Relationships: Created 1-to-many relationships between the primary keys of the dimensions (operating room dashboard) and the 
     transactions fact table(Date table).
     
  DAX Measures, & Volume Analysis
     Hourly Patterns: Analyzes peak hours for patient admissions and calculates average turnaround times per hour.
     Weekly Trends: Identifies the busiest days of the week, sorted chronologically from Sunday to Saturday.
     Monthly & Yearly Volume: Tracks the historical volume of total surgeries over time to spot long-term trends.
     Efficiency Rate: Calculates the exact percentage of turnarounds completed on or below the 25-minute target.
     Overage Metrics: Counts the total number of delayed incidents (turnarounds > 25 mins) and outputs the overall overage incident rate as a      percentage.
     Delay Tracking: Aggregates only the excess minutes spent beyond the threshold using the GREATEST(OR turnover time - 25, 0) function,  
     ensuring early turnarounds do not offset actual delays.
     Overage Financial Cost: Multiplies the total delayed minutes by a benchmark cost of 45 financial units per minute to quantify 
     operational waste.


