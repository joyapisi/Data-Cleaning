# 🇰🇪 Final Practical Examination

## Question One 
# Analytics Dashboard Interpretation (6 Marks)

A company launched a two-week online marketing campaign to promote a new product. The following dashboard summary was obtained from one of the analytics platforms studied during the semester (Matomo, Google Analytics, Adobe Analytics, Google Shopping, or Metricool).

| Metric | Value |
|---------|------:|
| Website Users | 4,850 |
| Sessions | 6,200 |
| Average Engagement Time | 2 min 18 sec |
| Bounce Rate | 38% |
| Product Page Views | 2,150 |
| Add-to-Cart Actions | 430 |
| Purchases | 120 |
| Conversion Rate | 2.5% |
| Instagram Reach | 18,400 |
| Instagram Engagement Rate | 6.2% |

Answer the following questions:

### (a) Dashboard Interpretation (2 Marks)

Identify **two** insights that can be drawn from the dashboard metrics.

---

### (b) Performance Evaluation (2 Marks)

Based on the metrics provided, evaluate whether the campaign was successful. Support your answer using evidence from the data.

---

### (c) Recommendations (2 Marks)

Recommend **two** actions that could improve the campaign's future performance. Briefly justify each recommendation using the dashboard metrics.

**(Total: 6 Marks)**

## Question Two
**Data Analytics Using R**

**Total Marks:** 18  
**Duration:** 4 Hours

---

# Background

Kenya has experienced significant growth in internet access, electricity connectivity, and economic development over the past two decades. In this practical examination, you will retrieve selected development indicators from the **World Bank API**, prepare the data for analysis, perform basic calculations, create visualisations, and interpret your findings using R.

---

# Learning Outcomes

By completing this examination, you should be able to:

- Retrieve real-world data using an API.
- Clean and prepare data for analysis.
- Perform basic analytical calculations.
- Create informative data visualisations using **ggplot2**.
- Interpret analytical findings using evidence from data.

---

# Research Question

> What trends can be observed in Kenya's economic and digital development between 2000 and 2024?

---

# Required Packages

Install the required packages (only if not already installed):

```r
install.packages(c(
  "WDI",
  "tidyverse",
  "scales"
))
```

Load the packages:

```r
library(WDI)
library(tidyverse)
library(scales)
```

---

# Data Retrieval

Retrieve Kenya's development data from the **World Bank API** for the period **2000–2024** using the following indicators:

| Variable | Indicator Code |
|-----------|----------------|
| GDP_Per_Capita | NY.GDP.PCAP.CD |
| Internet_Users | IT.NET.USER.ZS |
| Electricity_Access | EG.ELC.ACCS.ZS |
| Population | SP.POP.TOTL |

---

# Question 2(a): Data Preparation (5 Marks)

Create a cleaned dataframe named **`kenya_clean`**.

Your code should:

- Arrange the observations from the earliest to the latest year.
- Remove unnecessary country identification columns.
- Check for missing values.
- Produce a cleaned dataset suitable for analysis.

**(5 Marks)**

---

# Question 2(b): Data Analysis and Visualisation (9 Marks)

## (i) Annual Percentage Growth (3 Marks)

Calculate the annual percentage growth for:

- GDP per Capita
- Internet Users

Identify the year with the highest GDP per Capita growth.

**(3 Marks)**

---

## (ii) Create TWO Visualisations (6 Marks)

Create **any two** of the following charts:

- Line Chart
- Bubble Chart
- Correlation Heat Map
- Faceted Line Chart

Each chart must include:

- A descriptive title
- Axis labels
- Legend (where applicable)
- Caption showing the data source

**(6 Marks)**

---

# Question 2(c): Interpretation (4 Marks)

Write a **150–200-word** analytical summary discussing:

- Two important trends observed.
- One relationship between the variables.
- One limitation of the analysis.

Support your discussion using evidence from your charts.

**(4 Marks)**

---

# Submission Requirements

Submit the following before the examination deadline:

## 1. Shared Posit Cloud Project

Share your Posit Cloud project and submit the **Project URL**.

Ensure the project sharing permissions allow the examiner to access your work.

## 2. Project Files

Your project must include:

- `analysis.R`
- `kenya_clean.csv`
- Exported chart images (`.png`)
- Analytical report (`PDF`)

---

# Suggested Project Structure

```text
kenya-development-analysis/
│
├── analysis.R
├── kenya_clean.csv
├── charts/
│   ├── chart1.png
│   └── chart2.png
└── report/
    └── analysis-report.pdf
```

---

# Marking Scheme

| Task | Marks |
|------|------:|
| Question 1: Data Preparation | 5 |
| Question 2(a): Annual Growth Calculations | 3 |
| Question 2(b): Two Visualisations | 6 |
| Question 3: Interpretation | 4 |
| **Total** | **18 Marks** |

---

# Academic Integrity

- This examination is an individual assessment.
- All submitted code must be your own work.
- You may consult official R package documentation or AI chatbots for your code.
- You should be able to explain **the context** of your blocks of code if requested.
- Any external sources used must be appropriately acknowledged.
- Submissions that cannot be verified through the shared Posit Cloud project may receive reduced marks.
