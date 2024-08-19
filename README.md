# Employees-Attrition-Analysis
---
## Table of Contents
1. [Project Overview](#project-overview)
2. [Data Overview](#data-overview)
3. [Objectives](#objectives)
4. [SQL and Tableau Queries](#sql-and-tableau-queries)
    - [SQL Queries](#sql-queries)
    - [Tableau Queries](#tableau-queries)
5. [Tableau Visualization](#tableau-visualization)
6. [Insights and Recommendations](#insights-and-recommendations)
7. [Conclusion](#conclusion)
8. [Additional Resources](#additional-resources)

## Project Overview
This project aims to analyze HR data to identify patterns in employee attrition, job satisfaction, and department-wise performance. The analysis provides insights into workforce management and helps in formulating strategies to improve employee retention and satisfaction.

## Data Overview
- **HR_Data.csv:** This dataset includes employee information such as department, job role, education level, age group, and attrition rate. 
- [**Download the Dataset**](https://public.tableau.com/vizql/v_202422408070112/javascripts/hybrid-window/min/index.html?id=1i5lgvdcc%24b9sc-zb-71-59-hto2cv&moduleId=view_data)

## Objectives
- **Attrition Analysis:** Understand the factors contributing to employee attrition across different departments and demographics.
- **Job Satisfaction:** Evaluate employee job satisfaction ratings across various roles and departments.
- **Demographic Insights:** Analyze how age, gender, and education level impact attrition and satisfaction.
- **Actionable Insights:** Provide recommendations to improve employee retention and job satisfaction.

## SQL and Tableau Queries

### SQL Queries
Here are some SQL queries used to manage and analyze the HR dataset:

```sql
-- Create Database and Tables
CREATE DATABASE HRAnalyticsDB;

USE HRAnalyticsDB;

CREATE TABLE EmployeeData (
    EmployeeID INT PRIMARY KEY,
    Department VARCHAR(100),
    JobRole VARCHAR(100),
    EducationLevel VARCHAR(50),
    AgeGroup VARCHAR(50),
    Gender VARCHAR(10),
    Attrition INT,
    JobSatisfaction INT
);

-- Load Data
BULK INSERT EmployeeData
FROM 'path_to_your/HR_Data.csv'
WITH (FIELDTERMINATOR = ',', ROWTERMINATOR = '\n', FIRSTROW = 2);

-- Analyze Attrition by Department
SELECT 
    Department,
    COUNT(*) AS EmployeeCount,
    SUM(Attrition) AS AttritionCount,
    (SUM(Attrition) * 1.0 / COUNT(*)) * 100 AS AttritionRate
FROM EmployeeData
GROUP BY Department;
```

### Tableau Queries
In Tableau, calculated fields can be used to perform similar analyses. Below are equivalent queries:

```tableau
-- Attrition Rate Calculation
IF [Attrition] = 1 THEN 1 ELSE 0 END

-- Job Satisfaction Grouping
IF [JobSatisfaction] <= 2 THEN "Low"
ELSEIF [JobSatisfaction] = 3 THEN "Medium"
ELSE "High" END

-- Attrition by Department
{ FIXED [Department]: SUM([Attrition]) / COUNT([EmployeeID]) }

-- Attrition by Age Group
{ FIXED [AgeGroup]: SUM([Attrition]) / COUNT([EmployeeID]) }
```

## Tableau Visualization
The Tableau dashboard provides a comprehensive view of the following:

- **Employee Count and Attrition:** Overview of total employees, attrition rate, and active employees by department and demographic factors.
- **Job Satisfaction Rating:** Visual representation of job satisfaction across different job roles.
- **Department-wise Analysis:** Insight into attrition rates and satisfaction levels across various departments.
- **Demographic Insights:** Analysis of attrition rates based on age group, gender, and education level.

You can view the Tableau dashboard [here](https://public.tableau.com/app/profile/noe.careme.fouotsa.manfouo/viz/HRAnalytics_17211814963320/HRAnalyticsDashboard).

## Insights and Recommendations
Based on the analysis:

- **Departmental Attrition:** The R&D department has the highest attrition rate, suggesting the need for targeted retention strategies.
- **Job Satisfaction:** Sales executives show lower satisfaction levels, indicating a potential area for improvement in job roles or responsibilities.
- **Demographic Trends:** Employees aged 25-34 show the highest attrition rates, particularly males. Focused engagement strategies for this demographic could be beneficial.
- **Education Impact:** Employees with life sciences and medical backgrounds show higher attrition, suggesting a potential misalignment with job roles or expectations.

## Conclusion
This project delivers critical insights into employee attrition and job satisfaction, enabling HR teams to make data-driven decisions to improve workforce management and retention.

## Additional Resources
- [Download the Dataset](https://public.tableau.com/vizql/v_202422408070112/javascripts/hybrid-window/min/index.html?id=1i5lgvdcc%24b9sc-zb-71-59-hto2cv&moduleId=view_data)
- [View Tableau Dashboard](https://public.tableau.com/app/profile/noe.careme.fouotsa.manfouo/viz/HRAnalytics_17211814963320/HRAnalyticsDashboard)
- [Project Presentation](#)

---
