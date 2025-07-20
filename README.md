# DSA-Capstone-Project-2

This is where I documented my final project during my DSA data analysis training with Incubator Hub. I learnt a lot about using Ms Excel, SQL and Power BI to analyze various data sets in order to answer questions and make data-driven decisions.

## Project Topic: Palmoria Group HR Analysis

### Project Overview

This data analysis aims to apply my Power BI skills from DSA data analysis class in generating key insights from the employee data of Palmoria Group. By analyzing gender-related issues, salary gaps and compliance to regulation in the given data, we seek to gather enough insights which the management team would need to address the issue of gender equality in the company.

### Table of Contents

### Data Sources

The primary source of data used here are Palmoria Group emp-data.csv and Palmoria Group Bonus Rules.xlsx files. These were downloaded from the Learning Management System (LMS) used during the course of the training.

### Tools Used

Microsoft Power BI – Employed for creating interactive and visually appealing reports [Download Here](https://www.microsoft.com/en-us/download/details.aspx?id=58494)

### Data Cleaning and Preparation

The following was performed during the data cleaning and preparation phase;
- Data loading and inspection
    - Data was imported and taken to the power query editor for transformation. 
- Handling missing variables
    - Employees without salary were removed because they are no longer with the company.
    - Departments indicated as ‘NULL’ were removed. 
- Data cleaning and formatting
    - Empty rows in the gender column was replaced with ‘undisclosed’.

### Project Structure – Exploratory Data Analysis

EDA involved the exploration of the data to answer some questions about the data such as:
- What is the gender distribution in the organization? Distil to regions and departments
- Show insights on ratings based on gender 
- Analyze the company’s salary structure. Identify if there is a gender pay gap. If there is, identify the department and regions that should be the focus of management 
- A recent regulation was adopted which requires manufacturing companies to pay employees a minimum of $90,000 
    - Does Palmoria meet this requirement? 
    - Show the pay distribution of employees grouped by a band of $10,000. For example: 
    - How many employees fall into a band of $10,000 – $20,000, $20,000 – $30,000, etc.? 
    - Also visualize this by region.

### Data Analysis

Some of the DAX expressions used during the analysis are:
``` DAX
Total Employees = COUNTROWS (‘Palmoria Group emp-data’)

```
``` DAX
Gender Count = COUNT (‘Palmoria Group emp-data’ [Gender])

```

``` DAX
Salary Count = COUNT (‘Palmoria Group emp-data’[Salary])

```

``` DAX
Average Salary Count = AVERAGE (‘Palmoria Group emp-data’[Salary])

```

``` DAX
Employees below the minimum salary of $90,000 =
CALCULATE (COUNTROWS (‘Palmoria Group emp-data’), ‘Palmoria Group emp-data’ [Salary] < 90000)

```

``` DAX
% of Employees below the minimum salary of $90,000 =
DIVIDE ([Employees Below 90K], [Total Employees], 0)

```

```DAX
Salary Band = VAR Salary = 'Palmoria Group emp-data'[Salary] VAR BandStart = FLOOR(Salary, 10000)
RETURN FORMAT(BandStart, "$#,##0") & " - " & FORMAT(BandStart + 9999, "$#,##0))

```

### Result/ Findings

The following insights were derived from the analysis;
- Males are _2.53%_ more than females in the overall gender distribution while the employees whose gender were not disclosed make up _4.23%_ of the gender distribution.
- The _Kaduna_ branch of the company has about _17_ males more than females.

![Palmoria 1](https://github.com/user-attachments/assets/bacc2458-8c60-47ed-8c36-04d8a720c2ae)

- Across the departments, it was observed that _product management, support, services, legal and accounting departments_ had about _5%_ more males in comparison to females. Only _research and development department_ had _10%_ more females than males.

![Palmoria 2](https://github.com/user-attachments/assets/a3899102-a061-47bb-a067-55c1c4f32095)

- The company has more _“good” and “very good”_ employee rating from the _female_ gender while the _male_ gender has more _“average”, “very poor” and “poor”_ employee ratings when compared to the female gender.

![Palmoria 3](https://github.com/user-attachments/assets/f2e91012-abe3-4bb6-8db9-a3c6994129f3)

- From the analysis of the average salary of the company’s employees by gender across locations and departments. It was observed that the average salary of the male employees was _$3,000_ higher than the average salary of the female employees across the 3 branches of the company. Males are also paid higher in almost all the departments of the company except _engineering, training and marketing departments_ where females are paid higher than the male employees.

![Palmoria 4](https://github.com/user-attachments/assets/99cf68c9-f22a-434c-a45d-55cbdef292da)

![Palmoria 5](https://github.com/user-attachments/assets/91f49b6c-d698-4fdb-b537-490f1b2d7154)

- The company does not meet the $90,000 minimum salary regulation requirement. _Over 50%_ of her employees have salaries below the required minimum salary.

![Palmoria 6](https://github.com/user-attachments/assets/3c1989df-577f-483e-9de2-d5c88325b7d0)

![Palmoria 7](https://github.com/user-attachments/assets/ae8f7527-5749-4db2-a128-34b405e14ab4)

![Palmoria 8](https://github.com/user-attachments/assets/7fbf4387-e693-49bd-8bcd-18f0e2de9cde)

- Visuals for question 5

![Palmoria 9](https://github.com/user-attachments/assets/c59222ad-9138-44ac-8aab-9f1ea97690d3)

### Recommendations

- More females should be recruited in _product management, support, services, legal and accounting departments_ of the company in order to ensure gender equality.
- More females should be hired in the _Kaduna_ branch of the company.
- Giving the fact that the female employees have better employee ratings than the male employees, their salaries should be brought on a par with the salary of their male counterparts with added bonuses where applicable. This will not only bridge the gender pay gap but also encourage the employees to do their best.
- The company should find out the gender of the employees whose genders were not disclosed. The employees in this gender category were observed to have an average salary that is way higher than the salaries of both the male and female employees.
	
### Limitations

The undisclosed category of the gender may affect the accuracy of my conclusions. These employees could be either male or female but because their gender was not disclosed, the conclusions cannot be said to be 100% accurate.
