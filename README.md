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

### Dataset Columns

| Column            |
| ----------------- |
| Student Name      |
| Email             |
| Gender            |
| Age               |
| Course            |
| Attendance (%)    |
| Test Score        |
| Registration Date |

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
