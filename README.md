# Data Cleaning Assignment Using Excel

## Overview

This assignment introduces you to the practical process of data cleaning using Microsoft Excel or Google Sheets. Students will work in groups to identify and correct common data quality issues found in real-world datasets.

The goal is to develop foundational data preparation skills that are essential for data analysis, business intelligence, and artificial intelligence projects.

---

## Learning Outcomes

By the end of this assignment, students should be able to:

* Identify common data quality problems.
* Remove duplicate records.
* Standardize text and categorical values.
* Detect missing and invalid data.
* Use Excel formulas to validate and clean datasets.
* Create summary statistics from cleaned data.
* Document the data cleaning process.

---

## Software Requirements

* Microsoft Excel (Recommended)
* Google Sheets (Alternative)

---

## Dataset Description

Each group will receive a dataset containing student records with intentional errors.

### Dataset csv
``

```csv
Student Name,Email,Gender,Age,Course,Attendance %,Test Score,Registration Date
joy phoebe,JOY@GMAIL.COM,F,28,Data Analytics,95,78,12/01/2026
Joy Phoebe,joy@gmail.com,female,28,Data Analytics,95,78,Jan 12 2026
Peter Maina,peter@email,Male,150,Python for Data Analysis,88,67,2026-01-15
Mary Wanjiku,,female,24,AI Fundamentals,92,85,
John Kamau,john.kamau@gmail.com,M,22,Data Analytics,105,90,01-20-2026
Alice Njeri,ALICE@GMAIL.COM,Female,21,Machine Learning,89,91,2026/01/22
alice njeri,alice@gmail.com,F,21,Machine Learning,89,91,22 Jan 2026
David Ochieng,david@gmail.com,male,19,Python for Data Analysis,75,,2026-01-25
Grace Atieno,grace@gmail.com,F,18,AI Fundamentals,82,73,2026-01-28
Brian Kiptoo,brian@gmail.com,M,17,Data Analytics,-5,64,2026-01-29
Faith Chebet,faith@gmail.com,Female,20,Machine Learning,91,88,2026-02-01
Samuel Mwangi,samuel@gmail.com,Male,23,AI Fundamentals,87,79,2026-02-02
Rose Akinyi,rose@gmail,Female,25,Data Analytics,94,84,2026-02-03
Kevin Mutua,kevin@gmail.com,M,0,Python for Data Analysis,81,71,2026-02-04
Lilian Cherotich,lilian@gmail.com,F,26,Machine Learning,90,95,04/02/2026
Lilian Cherotich,lilian@gmail.com,F,26,Machine Learning,90,95,04/02/2026
James Kariuki,james@gmail.com,Male,30,AI Fundamentals,85,77,2026-02-06
Mercy Wambui,mercy@gmail.com,Female,22,Data Analytics,96,89,2026-02-07
Tom Odhiambo,tom@gmail.com,M,24,Python for Data Analysis,78,82,07-02-2026
Anne Nyokabi,anne@gmail.com,Female,19,Machine Learning,88,93,2026/02/08
George Otieno, george@gmail.com ,Male,27,AI Fundamentals,92,86,February 8 2026
Sarah Chepkemoi,sarah@gmail.com,F,200,Data Analytics,90,80,2026-02-09
Paul Kibet,paul@gmail.com,M,21,Python for Data Analysis,83,76,2026-02-10
Nancy Moraa,nancy@gmail.com,Female,23,Machine Learning,110,87,2026-02-11
Dennis Kimani,dennis@gmail.com,Male,25,AI Fundamentals,89,,2026-02-12
Beatrice Achieng,beatrice@gmail.com,F,20,Data Analytics,93,92,2026-02-13
Victor Mwenda,victor@gmail.com,M,18,Python for Data Analysis,86,68,13/02/2026
Cynthia Jepkosgei,cynthia@gmail.com,Female,24,Machine Learning,84,90,2026-02-14
Mark Kiprotich,mark@gmail.com,Male,22,AI Fundamentals,79,74,2026-02-15
Jane Naliaka,,F,21,Data Analytics,88,81,2026-02-16
```



---

## Common Data Issues Included

The dataset contains several common data quality problems such as:

* Duplicate student records
* Missing email addresses
* Inconsistent capitalization
* Extra spaces before or after text
* Invalid ages (e.g., 150 years)
* Inconsistent gender entries (`F`, `female`, `M`, `male`)
* Attendance values above 100%
* Missing test scores
* Different date formats

---

## Assignment Instructions

### Step 1: Open the Dataset

Open the provided dataset in Microsoft Excel or Google Sheets.

---

### Step 2: Create a Working Copy

Duplicate the original worksheet and rename it:

```text
Cleaned Data
```

Keep the original sheet unchanged.

---

### Step 3: Remove Duplicate Records

Navigate to:

```text
Data → Remove Duplicates
```

Remove any duplicate student records.

---

### Step 4: Standardize Student Names

Use the following formula to remove extra spaces and standardize capitalization:

```excel
=PROPER(TRIM(A2))
```

---

### Step 5: Convert Emails to Lowercase

Use:

```excel
=LOWER(TRIM(B2))
```

---

### Step 6: Standardize Gender Values

Use:

```excel
=IF(OR(C2="F",C2="female"),"Female",
IF(OR(C2="M",C2="male"),"Male","Check"))
```

---

### Step 7: Validate Student Ages

Use:

```excel
=IF(OR(D2<15,D2>80),"Invalid","Valid")
```

Flag unrealistic ages for review.

---

### Step 8: Validate Attendance Percentages

Use:

```excel
=IF(OR(F2<0,F2>100),"Invalid","Valid")
```

Attendance values must fall between 0 and 100.

---

### Step 9: Highlight Missing Values

Use Conditional Formatting:

```text
Home → Conditional Formatting → Highlight Blank Cells
```

Identify records with missing information.

---

### Step 10: Create a Summary Table

Create a summary section showing:

* Total number of students
* Number of duplicate records removed
* Number of missing emails
* Number of invalid ages
* Average test score
* Highest test score
* Lowest test score

---

## Deliverables

Each group must submit:

### 1. Cleaned Dataset

A cleaned Excel workbook containing:

* Original dataset
* Cleaned dataset

### 2. Group Report done in One Paragraph

The report should include:
* Corrections made on the data set
* Challenges encountered

## Assessment Criteria

| Criteria                       | Marks   |
| ------------------------------ | ------- |
| Data Cleaning Accuracy         | 15      |
| Correct Use of Excel Functions | 10      |
| Summary Statistics             | 5      |
| **Total**                      | **30** |

---

## Submission Guidelines

Submit the following files:

```text
GroupName_CleanedData.xlsx
GroupName_Report.doc
```

Ensure all files are submitted before the deadline provided by the instructor.

---

## Good Luck!

Remember: In data analysis, clean data leads to reliable insights. Focus on accuracy, consistency, and documentation throughout the cleaning process.
