# 🇰🇪 Advanced R Assignment: Kenya’s Digital Development and Economic Transformation

## Background

Kenya has experienced major changes in internet access, mobile connectivity, urbanisation, employment, and economic growth. In this assignment, you will retrieve Kenyan development indicators from the **World Bank API**, clean and transform the dataset, calculate new variables, and produce advanced visualisations using R.

This assignment is more challenging because it requires:

- Working with multiple indicators
- Reshaping data
- Handling missing values
- Calculating percentage change
- Creating a development index
- Producing complex charts
- Interpreting relationships between variables

---

## Learning Outcomes

By the end of the assignment, you should be able to:

- Retrieve real-world Kenyan data using an API
- Clean and validate a multivariable dataset
- Reshape data between wide and long formats
- Calculate annual growth rates
- Standardise variables
- Create a composite development index
- Produce heat maps, faceted charts, bubble charts, and slope charts
- Interpret correlations without assuming causation
- Communicate findings through data storytelling

---

# Research Question

> How have internet access, urbanisation, employment, electricity access, and income changed in Kenya, and what relationships exist between these indicators?

---

## Required Packages

Install the packages once:

```r
install.packages(c(
  "WDI",
  "tidyverse",
  "scales",
  "corrplot"
))
```

Load the packages:

```r
library(WDI)
library(tidyverse)
library(scales)
library(corrplot)
```

---

# Part 1: Retrieve Kenya’s Development Data

Use the following World Bank indicators:

| Variable | Indicator code | Meaning |
|---|---|---|
| GDP_Per_Capita | `NY.GDP.PCAP.CD` | GDP per capita in current US dollars |
| Internet_Users | `IT.NET.USER.ZS` | Percentage of people using the internet |
| Urban_Population | `SP.URB.TOTL.IN.ZS` | Urban population as a percentage of total population |
| Electricity_Access | `EG.ELC.ACCS.ZS` | Percentage of the population with access to electricity |
| Unemployment | `SL.UEM.TOTL.ZS` | Total unemployment rate |
| Life_Expectancy | `SP.DYN.LE00.IN` | Life expectancy at birth |
| Population | `SP.POP.TOTL` | Total population |

Download the data for Kenya from **2000 to 2024**.

```r
kenya_data <- WDI(
  country = "KEN",
  indicator = c(
    GDP_Per_Capita = "NY.GDP.PCAP.CD",
    Internet_Users = "IT.NET.USER.ZS",
    Urban_Population = "SP.URB.TOTL.IN.ZS",
    Electricity_Access = "EG.ELC.ACCS.ZS",
    Unemployment = "SL.UEM.TOTL.ZS",
    Life_Expectancy = "SP.DYN.LE00.IN",
    Population = "SP.POP.TOTL"
  ),
  start = 2000,
  end = 2024
)
```

Inspect the dataset:

```r
head(kenya_data)
str(kenya_data)
summary(kenya_data)
```

---

# Task 1: Data Validation and Cleaning — 10 Marks

Create a cleaned dataframe called `kenya_clean`.

Your code must:

1. Arrange the observations from the earliest to the latest year.
2. Remove unnecessary country identification columns.
3. Check for duplicate years.
4. Count missing values in every variable.
5. Identify which years have incomplete observations.
6. Decide whether to remove, retain, or estimate missing values.
7. Explain your decision in a short code comment.

Suggested starting point:

```r
kenya_clean <- kenya_data |>
  select(
    year,
    GDP_Per_Capita,
    Internet_Users,
    Urban_Population,
    Electricity_Access,
    Unemployment,
    Life_Expectancy,
    Population
  ) |>
  arrange(year)
```

Check missing values:

```r
colSums(is.na(kenya_clean))
```

Identify incomplete rows:

```r
kenya_clean |>
  filter(if_any(everything(), is.na))
```

---

# Task 2: Descriptive Statistical Analysis — 10 Marks

Calculate the following statistics for every numeric indicator:

- Minimum
- Maximum
- Mean
- Median
- Standard deviation
- Number of missing observations

Create one summary table.

Suggested structure:

```r
summary_table <- kenya_clean |>
  summarise(
    across(
      -year,
      list(
        Minimum = ~ min(.x, na.rm = TRUE),
        Maximum = ~ max(.x, na.rm = TRUE),
        Mean = ~ mean(.x, na.rm = TRUE),
        Median = ~ median(.x, na.rm = TRUE),
        SD = ~ sd(.x, na.rm = TRUE),
        Missing = ~ sum(is.na(.x))
      )
    )
  )
```

Present the results in a readable format.

---

# Task 3: Calculate Annual Change — 10 Marks

Calculate annual percentage change for:

- GDP per capita
- Internet users
- Electricity access
- Population

Use the formula:

\[
\text{Percentage Change} =
\frac{\text{Current Value} - \text{Previous Value}}
{\text{Previous Value}}
\times 100
\]

Example:

```r
kenya_change <- kenya_clean |>
  arrange(year) |>
  mutate(
    GDP_Growth = (
      GDP_Per_Capita - lag(GDP_Per_Capita)
    ) / lag(GDP_Per_Capita) * 100,

    Internet_Growth = (
      Internet_Users - lag(Internet_Users)
    ) / lag(Internet_Users) * 100,

    Electricity_Growth = (
      Electricity_Access - lag(Electricity_Access)
    ) / lag(Electricity_Access) * 100,

    Population_Growth = (
      Population - lag(Population)
    ) / lag(Population) * 100
  )
```

Answer:

1. Which year had the largest increase in GDP per capita?
2. Which year had the largest decline in GDP per capita?
3. Which year had the fastest internet-user growth?
4. Was population growth stable throughout the period?

---

# Task 4: Reshape the Dataset — 8 Marks

Transform the dataset from wide format to long format.

```r
kenya_long <- kenya_clean |>
  pivot_longer(
    cols = -year,
    names_to = "Indicator",
    values_to = "Value"
  )
```

Display:

```r
head(kenya_long)
```

Explain the difference between:

- Wide data
- Long data
- Why long data is useful in `ggplot2`

---

# Task 5: Faceted Development Trends — 12 Marks

Create a faceted line chart showing the trend of:

- Internet users
- Urban population
- Electricity access
- Unemployment
- Life expectancy

Each variable should appear in its own panel.

```r
percentage_data <- kenya_clean |>
  select(
    year,
    Internet_Users,
    Urban_Population,
    Electricity_Access,
    Unemployment,
    Life_Expectancy
  ) |>
  pivot_longer(
    cols = -year,
    names_to = "Indicator",
    values_to = "Value"
  )
```

Create the chart:

```r
ggplot(
  percentage_data,
  aes(x = year, y = Value)
) +
  geom_line(linewidth = 1) +
  geom_point() +
  facet_wrap(
    ~ Indicator,
    scales = "free_y"
  ) +
  labs(
    title = "Kenya’s Development Indicators",
    subtitle = "Changes in connectivity, urbanisation, employment and health",
    x = "Year",
    y = "Indicator value"
  ) +
  theme_minimal()
```

Your final chart must include:

- A meaningful title
- A subtitle
- Readable axis labels
- A caption identifying the World Bank as the data source
- Appropriate theme adjustments

---

# Task 6: Correlation Heat Map — 12 Marks

Create a correlation matrix using the numeric development indicators.

```r
kenya_correlations <- kenya_clean |>
  select(-year) |>
  cor(
    use = "pairwise.complete.obs"
  )
```

Convert the matrix into long format:

```r
correlation_data <- as.data.frame(kenya_correlations) |>
  rownames_to_column("Variable_1") |>
  pivot_longer(
    cols = -Variable_1,
    names_to = "Variable_2",
    values_to = "Correlation"
  )
```

Create the heat map:

```r
ggplot(
  correlation_data,
  aes(
    x = Variable_1,
    y = Variable_2,
    fill = Correlation
  )
) +
  geom_tile() +
  geom_text(
    aes(label = round(Correlation, 2))
  ) +
  labs(
    title = "Correlation Heat Map of Kenya’s Development Indicators",
    x = NULL,
    y = NULL,
    fill = "Correlation"
  ) +
  theme_minimal() +
  theme(
    axis.text.x = element_text(
      angle = 45,
      hjust = 1
    )
  )
```

Interpret at least three relationships.

Your discussion must distinguish between:

- Positive correlation
- Negative correlation
- Strong correlation
- Weak correlation
- Correlation and causation

---

# Task 7: Kenya Digital Development Bubble Chart — 10 Marks

Create a bubble chart with:

- X-axis: Internet users
- Y-axis: GDP per capita
- Bubble size: Population
- Bubble label or colour grouping: Year period

Create a period variable:

```r
kenya_bubble <- kenya_clean |>
  mutate(
    Period = case_when(
      year <= 2005 ~ "2000–2005",
      year <= 2010 ~ "2006–2010",
      year <= 2015 ~ "2011–2015",
      year <= 2020 ~ "2016–2020",
      TRUE ~ "2021–2024"
    )
  )
```

Chart starter:

```r
ggplot(
  kenya_bubble,
  aes(
    x = Internet_Users,
    y = GDP_Per_Capita,
    size = Population,
    colour = Period
  )
) +
  geom_point(alpha = 0.7) +
  scale_y_continuous(
    labels = label_dollar()
  ) +
  scale_size_continuous(
    labels = label_number(
      scale = 0.000001,
      suffix = "M"
    )
  ) +
  labs(
    title = "Internet Access and GDP per Capita in Kenya",
    subtitle = "Bubble size represents Kenya’s population",
    x = "Internet users (% of population)",
    y = "GDP per capita",
    size = "Population",
    colour = "Period",
    caption = "Source: World Bank Development Indicators"
  ) +
  theme_minimal()
```

Interpret:

1. What happens to GDP per capita as internet use increases?
2. Is the relationship perfectly linear?
3. What other factors may explain changes in GDP per capita?
4. How does population growth affect the visual interpretation?

---

# Task 8: Create a Digital Development Index — 15 Marks

Create a simple index using:

- Internet users
- Electricity access
- GDP per capita
- Life expectancy

First, standardise the variables using z-scores:

```r
kenya_index <- kenya_clean |>
  mutate(
    Internet_Z = as.numeric(scale(Internet_Users)),
    Electricity_Z = as.numeric(scale(Electricity_Access)),
    GDP_Z = as.numeric(scale(GDP_Per_Capita)),
    Life_Expectancy_Z = as.numeric(scale(Life_Expectancy))
  )
```

Create the index:

```r
kenya_index <- kenya_index |>
  mutate(
    Development_Index = rowMeans(
      cbind(
        Internet_Z,
        Electricity_Z,
        GDP_Z,
        Life_Expectancy_Z
      ),
      na.rm = TRUE
    )
  )
```

Create a line chart showing the index over time:

```r
ggplot(
  kenya_index,
  aes(
    x = year,
    y = Development_Index
  )
) +
  geom_line(linewidth = 1.2) +
  geom_point() +
  geom_hline(
    yintercept = 0,
    linetype = "dashed"
  ) +
  labs(
    title = "Kenya Digital Development Index",
    subtitle = "Combined standardised measure of connectivity, electricity, income and health",
    x = "Year",
    y = "Development Index",
    caption = "Index developed for educational purposes using World Bank indicators"
  ) +
  theme_minimal()
```

Explain:

1. Why standardisation is necessary.
2. What a score above zero means.
3. What a score below zero means.
4. The limitations of giving every indicator equal weight.
5. Whether this index is sufficient for measuring national development.

---

# Task 9: Before-and-After Comparison — 8 Marks

Compare the earliest available year with the most recent complete year.

Create a comparison table showing:

- GDP per capita
- Internet users
- Urban population
- Electricity access
- Unemployment
- Life expectancy
- Population

Calculate both:

- Absolute difference
- Percentage difference

Suggested approach:

```r
comparison_data <- kenya_clean |>
  filter(
    year %in% c(
      min(year),
      max(year)
    )
  )
```

Create either:

- A slope chart
- A dumbbell chart
- A grouped comparison chart

Explain which indicators improved and which indicators remained challenging.

---

# Task 10: Data Storytelling Report — 15 Marks

Write a report of **400–600 words** answering:

> To what extent has Kenya’s digital growth been accompanied by broader economic and social development?

Your report must include:

- A clear introduction
- At least four findings supported by data
- Reference to at least three charts
- Discussion of one unexpected result
- A warning about correlation and causation
- Limitations of the dataset
- A clear conclusion

Do not merely describe what is visible in each chart. Explain what the patterns may mean.

---

# Required Visualisations

Your project must contain at least:

1. Faceted line chart
2. Correlation heat map
3. Bubble chart
4. Development-index line chart
5. Before-and-after comparison chart

All charts must include:

- Title
- Axis labels
- Legend where necessary
- Data-source caption
- Consistent visual design
- Readable text

---

# GitHub Repository Structure

```text
kenya-digital-development-analysis/
│
├── README.md
├── kenya-development-analysis.R
├── data/
│   └── kenya-development-data.csv
├── charts/
│   ├── faceted-trends.png
│   ├── correlation-heatmap.png
│   ├── internet-gdp-bubble-chart.png
│   ├── development-index.png
│   └── before-after-comparison.png
└── report/
    └── kenya-development-report.pdf
```

Export the cleaned dataset:

```r
write.csv(
  kenya_clean,
  "data/kenya-development-data.csv",
  row.names = FALSE
)
```

Export a chart:

```r
ggsave(
  filename = "charts/correlation-heatmap.png",
  width = 10,
  height = 7,
  dpi = 300
)
```

---

# Submission Requirements

Submit the GitHub repository link containing:

- Completed `README.md`
- Fully commented R script
- Cleaned CSV dataset
- Five exported charts
- A 400–600-word analytical report
- Correct folder organisation
- Meaningful commit history

Your repository must contain at least **five commits**. Avoid submitting the entire project in one final commit.

Example commit messages:

```text
Add World Bank data retrieval code
Clean Kenya development indicators
Create correlation heat map
Calculate digital development index
Complete findings and documentation
```

---

# Marking Scheme

| Section | Marks |
|---|---:|
| Data validation and cleaning | 10 |
| Descriptive statistics | 10 |
| Annual change calculations | 10 |
| Data reshaping | 8 |
| Faceted trends chart | 12 |
| Correlation heat map | 12 |
| Bubble chart | 10 |
| Development index | 15 |
| Before-and-after comparison | 8 |
| Written data story | 15 |
| **Total** | **110 marks** |

The final score can be converted to a percentage:

```r
percentage_score <- student_score / 110 * 100
```

---

# Academic Integrity

You may consult official R documentation and package documentation. However:

- All submitted code must be understood by the student.
- Every chart interpretation must be written in the student’s own words.
- Any additional data sources must be acknowledged.
- Generated code that cannot be explained during assessment may not receive marks.
