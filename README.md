# Employees-Attrition-Analysis
---
## Table of Contents
1. [Project Overview](#project-overview)
2. [Data Overview](#data-overview)
3. [Business Case](#business-case)
4. [Objectives](#objectives)
5. [SQL and Tableau Queries](#sql-and-tableau-queries)
    - [SQL Queries](#sql-queries)
    - [Tableau Queries](#tableau-queries)
6. [Tableau Visualization](#tableau-visualization)
7. [Key Insights](#key-insights)
8. [Impact](#impact)
9. [Conclusion](#conclusion)
10. [Additional Resources](#additional-resources)

## Project Overview
The HR Analytics Dashboard is an interactive tool designed to provide comprehensive insights into employee attrition and job satisfaction within an organization. By visualizing key metrics such as attrition count, employee count, attrition rate, active employees, and average age, this dashboard helps HR departments make data-driven decisions. The analysis also includes attrition breakdowns by department, field, gender, age group, education level, and job role, providing a holistic view of the workforce.

## Data Overview
- **HR_Data.csv:** This dataset contains employee information, including department, job role, education level, age group, gender, and attrition status.
- [**Download the Dataset**](https://public.tableau.com/vizql/v_202422408070112/javascripts/hybrid-window/min/index.html?id=1i5lgvdcc%24b9sc-zb-71-59-hto2cv&moduleId=view_data)

## Business Case
Understanding and managing employee attrition is crucial for maintaining a stable and productive workforce. This project aims to empower HR departments with actionable insights into employee turnover and satisfaction, enabling them to:

- **Identify At-Risk Employees:** Pinpoint departments and demographics with high attrition rates, allowing for focused retention efforts.
- **Enhance Employee Satisfaction:** Monitor job satisfaction ratings to identify areas needing improvement and boost employee morale.
- **Support Strategic Planning:** Align HR strategies with organizational goals, fostering workforce stability and increasing productivity.

## Objectives
- **Attrition Analysis:** Explore the factors contributing to employee attrition across different departments and demographics.
- **Job Satisfaction Evaluation:** Assess employee job satisfaction ratings across various roles and departments.
- **Demographic Insights:** Understand how age, gender, and education level influence attrition and job satisfaction.
- **Actionable Recommendations:** Provide data-driven recommendations to improve employee retention and satisfaction.

## SQL and Tableau Queries

### SQL Queries
The following SQL queries were used to manage and analyze the HR dataset:

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
In Tableau, the following calculated fields were used to perform the analysis:

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
The Tableau dashboard offers a detailed visual representation of:

- **Employee Count and Attrition:** A comprehensive overview of total employees, attrition rates, and active employees by department and demographic factors.
- **Job Satisfaction Ratings:** Visual insights into job satisfaction across different job roles.
- **Department-wise Analysis:** In-depth analysis of attrition rates and satisfaction levels across various departments.
- **Demographic Insights:** Exploration of attrition rates based on age group, gender, and education level.

You can view the Tableau dashboard [here](https://public.tableau.com/app/profile/noe.careme.fouotsa.manfouo/viz/HRAnalytics_17211814963320/HRAnalyticsDashboard).

## Key Insights
- **Overall Attrition Rate:** The organization has an attrition rate of 16.12%, with 237 employees leaving out of 1,470.
- **Department-wise Attrition:** The highest attrition is observed in the Sciences department (89 employees), followed by Medical (63) and Marketing (35).
- **Gender-wise Attrition:** Male employees account for 150 of the departures, while female employees account for 87.
- **Age Group Distribution:** The 30-year age group has the highest number of employees (622), followed by the 40-year age group (349).
- **Job Satisfaction:** Laboratory Technicians and Research Scientists report higher job satisfaction, while Sales Executives have mixed ratings.
- **Field-wise Attrition:** The highest attrition is in the Sciences field, indicating a need for targeted retention strategies.

## Impact
- **Improved Retention Strategies:** By identifying high-risk areas and demographics, the organization can implement targeted initiatives to reduce turnover.
- **Enhanced Job Satisfaction:** Insights into job satisfaction enable HR departments to address specific issues, improving overall employee engagement and productivity.
- **Cost Savings:** Effective retention strategies can lead to significant cost savings by reducing the need for recruitment and training of new employees.
- **Data-Driven Decision Making:** The dashboard supports HR in making informed decisions that align with organizational goals, enhancing workforce management.
- **Predictive Analytics:** Over time, the dashboard can be enhanced with predictive analytics to forecast future attrition trends and proactively manage workforce challenges.

## Conclusion
The HR Analytics Dashboard provides essential insights into employee attrition and job satisfaction, empowering HR teams to make data-driven decisions that improve workforce management and retention.

## Additional Resources
- [Download the Dataset](https://public.tableau.com/vizql/v_202422408070112/javascripts/hybrid-window/min/index.html?id=1i5lgvdcc%24b9sc-zb-71-59-hto2cv&moduleId=view_data)
- [View Tableau Dashboard](https://public.tableau.com/app/profile/noe.careme.fouotsa.manfouo/viz/HRAnalytics_17211814963320/HRAnalyticsDashboard)
- [Project Presentation](#)

---
