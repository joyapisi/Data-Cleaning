# 🏥 Healthcare Data Analysis Using Posit Cloud

This repository contains a practical data analysis assignment completed using **Posit Cloud (RStudio Cloud)** and the **R programming language**. The project demonstrates a complete data analysis workflow, from setting up a cloud-based development environment to importing, cleaning, analyzing, and visualizing healthcare data.

---

## 📌 Objective

The objective of this practical is to familiarize students with the fundamentals of data analysis using R in Posit Cloud. Students will learn how to:

* Create and configure a Posit Cloud account.
* Create an R project.
* Import a healthcare dataset.
* Explore and clean the data.
* Generate descriptive statistics.
* Create visualizations using `ggplot2`.
* Interpret findings and document the analysis.

---

## 📚 Learning Outcomes

After completing this practical, students should be able to:

* Use Posit Cloud as a cloud-based R development environment.
* Install and load R packages.
* Import CSV datasets into R.
* Perform exploratory data analysis.
* Identify and handle missing values.
* Produce meaningful charts and graphs.
* Share reproducible analysis through GitHub.

---

# Assignment Tasks (15 Marks)

## 1. Create a Posit Cloud Account (1 Mark)

* Visit https://posit.cloud
* Register using your email address or Google account.
* Verify your account.

**Evidence:** Screenshot of your Posit Cloud dashboard.

---

## 2. Create a New Project (1 Mark)

Create a new **Blank R Project** named:

```text
Healthcare_Data_Analysis
```

**Evidence:** Screenshot of the project workspace.

---

## 3. Install Required Packages (1 Mark)

Install the required packages:

```r
install.packages("tidyverse")
install.packages("ggplot2")
```

Load the packages:

```r
library(tidyverse)
library(ggplot2)
```

---

## 4. Import the Dataset (1 Mark)

Download a healthcare dataset in CSV format and import it into your project.

Example:

```r
health <- read.csv("health_data.csv")
head(health)
```

---

## 5. Explore the Dataset (1 Mark)

Display the structure and summary of the dataset.

```r
str(health)
summary(health)
```

Report:

* Number of rows
* Number of columns
* Data types of each variable

---

## 6. Check for Missing Values (1 Mark)

Determine whether the dataset contains missing values.

```r
colSums(is.na(health))
```

Briefly explain your findings.

---

## 7. Clean the Dataset (1 Mark)

Remove rows containing missing values.

```r
health_clean <- na.omit(health)
```

---

## 8. Generate Descriptive Statistics (1 Mark)

Produce summary statistics.

```r
summary(health_clean)
```

Include:

* Mean
* Median
* Minimum
* Maximum

---

## 9. Create a Bar Chart (1 Mark)

Visualize disease cases by county.

```r
ggplot(health_clean,
       aes(x = County,
           y = Cases)) +
  geom_col()
```

Provide a short interpretation.

---

## 10. Create a Histogram (1 Mark)

Display the age distribution.

```r
ggplot(health_clean,
       aes(Age)) +
  geom_histogram()
```

Comment on the distribution.

---

## 11. Create a Scatter Plot (1 Mark)

Compare two numerical variables.

```r
ggplot(health_clean,
       aes(Age, Cases)) +
  geom_point()
```

Describe any relationship observed.

---

## 12. Create a Box Plot (1 Mark)

Identify possible outliers.

```r
ggplot(health_clean,
       aes(x = "Patients",
           y = Age)) +
  geom_boxplot()
```

Interpret the results.

---

## 13. Draw Insights (1 Mark)

Write **three key observations** based on your analysis.

Example:

* County A recorded the highest number of reported disease cases.
* Most patients were between 25 and 45 years old.
* Only a few age-related outliers were identified.

---

## 14. Save Your Script (1 Mark)

Save your R script as:

```text
Healthcare_Analysis.R
```

Upload it to this GitHub repository.

---

## 15. Document the Project (1 Mark)

Update this repository with:

* Project title
* Objective
* Dataset description
* Packages used
* Analysis steps
* Visualizations
* Findings
* Conclusion

---

# Repository Structure

```text
Healthcare-Data-Analysis/
│
├── README.md
├── Healthcare_Analysis.R
├── health_data.csv
└── images/
    ├── barchart.png
    ├── histogram.png
    ├── scatterplot.png
    └── boxplot.png
```

---

# Deliverables

By the end of this practical, the repository should contain:

* ✅ Completed Posit Cloud project
* ✅ R analysis script (`Healthcare_Analysis.R`)
* ✅ Healthcare dataset (`health_data.csv`)
* ✅ Four data visualizations
* ✅ Well-documented `README.md`

---

# Conclusion

This practical demonstrates the complete data analysis workflow using **Posit Cloud** and **R**. It covers environment setup, data import, cleaning, exploratory data analysis, visualization, interpretation, and documentation. These skills form the foundation of reproducible data analysis and are applicable to real-world datasets from healthcare, government, business, and research sectors.
