# NYPD_Arrests


## Introduction

The NYC Arrests dataset provides a comprehensive overview of every arrest made by the New York City Police Department (NYPD) during the current year. This dataset is meticulously compiled and manually extracted on a quarterly basis, with each record representing an individual arrest. The data is carefully reviewed by the Office of Management Analysis and Planning to ensure accuracy and reliability.

Each entry in the dataset includes detailed information about the type of crime committed, the specific location where the arrest took place, and the time of enforcement. Additionally, the dataset captures important demographic details about the suspects, offering insights into the characteristics of individuals involved in these incidents.


## Alteryx Workflow

![image](https://github.com/user-attachments/assets/68a1e64a-ebad-401c-989b-422a032acace)


## **Data Quality Assessment**

### **Identified Issues**

**1. Missing Values**

| Column Name   | Missing Value Count | Missing Value % |
|--------------|--------------------|----------------|
| LAW_CAT_CODE | 1390               | 0.53%         |
| KY_CD        | 32                 | <0.1%         |
| PD_CD        | 8                  | <0.1%         |
| Latitude     | 4                  | <0.1%         |
| Longitude    | 4                  | <0.1%         |


**2.	Column Name:** LAW_CAT_CD

   - Contains the following values: F, M, V, I, 9, and NULL
   - According to the metadata, only three values are valid: Felony (F), Misdemeanor (M), and Violation (V)
   - Problem: Presence of invalid categories (I, 9, and NULL) indicates data entry errors or undocumented classifications

**3.	Column Name:** X_COORD_CD , Y_COORD_CD

  - Zero values observed, which are not valid coordinates
  - Problem: These zeros likely indicate missing or incorrect data, which could impact spatial analyses

**4.	Column Name:** Latitude and Longitude
    
  - Contains 0 and NULL values, which are not valid geographical coordinates
  -  Problem: Invalid geolocation data could lead to inaccuracies in mapping and spatial insights




## **Action Plan for Data Cleaning using Staging Data Pipeline**

**1.	Column Name: LAW_CAT_CD**
  - Replace invalid values (I, 9, and NULL) with 'Unknown' to maintain consistency and allow categorization without data loss
  - Implement a validation rule in the pipeline to enforce category constraints: F, M, and V

**2.	Column Name: X_COORD_CD , Y_COORD_CD**
  - Replace zero values with the column's average, calculated dynamically within the pipeline to ensure updated and consistent imputation
  - Ensure no negative or non-numeric values are present by applying data validation checks

**3.	Column Name: Latitude and Longitude**
  - Replace 0 and NULL values with the average of their respective columns
  - Implement validation to ensure coordinates fall within the expected geographical range for NYC




## Physical Model - ER Studio

![image](https://github.com/user-attachments/assets/bafafced-d7b8-43dc-add2-806755a68057)


## Interactive Dashboards - Viz for deeper insights on NYPD Crime Data

### Time-Based Analysis

![image](https://github.com/user-attachments/assets/209a41b8-d5af-4cde-a25a-da761369a6e4)

### CrimeType-Based Analysis

![image](https://github.com/user-attachments/assets/0c2cbf64-ee89-43bc-9633-f3463001e3e2)

### Geographical Analysis

![image](https://github.com/user-attachments/assets/a45d15cf-aa4c-4ef4-8a84-bf7d5af352b5)

### Demographic Analysis

![image](https://github.com/user-attachments/assets/2d36e9fe-7180-4d87-9047-1cd3cb832afb)

### Predictive Analysis

![image](https://github.com/user-attachments/assets/21517c8d-00d2-4f8c-ad2f-a776cf8cba62)
