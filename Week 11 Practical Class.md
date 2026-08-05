# Final Class Practicals- Week 11

## Visualising Data From a CSV File
#### The Clean Dataset 
This dataset is to be inserted into a CSV file.

```
Order_ID,Date,Product_Category,Product_Name,Quantity,Price,Customer_City,Revenue
001,2024-01-03,Wall Art,Abstract Mural,2,1500,Nairobi,3000
002,2024-01-05,LED Mirror,LED Oval Mirror,1,4500,Kisumu,4500
003,2024-01-06,Wall Art,Nature Mural,1,2000,Nairobi,2000
004,2024-01-07,Wall Art,Botanical Mural,2,1800,Nairobi,3600
005,2024-01-08,LED Mirror,Round LED Mirror,1,,Mombasa,
006,2024-01-09,Wallpaper,Marble Wallpaper,,2500,Kisumu,
007,2024-01-10,Wallpaper,Floral Wallpaper,3,1200,Kisumu,3600
008,2024-01-11,Wall Sticker,Kids Wall Sticker,5,300,Nakuru,1500
009,2024-01-12,Wall Sticker,Animal Sticker Set,4,350,Nakuru,1400
010,2024-01-13,LED Mirror,Oval LED Mirror,1,5000,Mombasa,5000
011,2024-01-14,LED Mirror,Oval LED Mirror,1,5000,Mombasa,5000
012,2024-01-15,Wall Art,Abstract Mural,2,1500,Nairobi,3000
013,2024-01-16,Wallpaper,Wood Texture Wallpaper,2,2200,Eldoret,4400
014,2024-01-17,Wallpaper,Concrete Wallpaper,1,2100,Eldoret,2100
015,2024-01-18,LED Mirror,Square LED Mirror,1,,Kisumu,
```

### R Codes 
#### Histogram (Distribution of Product Prices)
Please note that sales_clean is the name of your CSV file and can be replaced with the correct name that you named your CSV file with. 

```R
library(ggplot2)

ggplot(sales_clean, aes(x = Price)) +
  geom_histogram(binwidth = 500, fill = "skyblue", color = "black") +
  labs(
    title = "Distribution of Product Prices",
    x = "Price",
    y = "Frequency"
  ) +
  theme_minimal()
```
#### Pie Chart (Products Sold by Category)
```R
library(dplyr)
library(ggplot2)

pie_data <- sales_clean %>%
  group_by(Product_Category) %>%
  summarise(Total_Quantity = sum(Quantity, na.rm = TRUE))

ggplot(pie_data, aes(x = "", y = Total_Quantity, fill = Product_Category)) +
  geom_col(width = 1) +
  coord_polar(theta = "y") +
  labs(
    title = "Products Sold by Category",
    fill = "Product Category"
  ) +
  theme_void()
```
# Visualising Data From WDI
### Installing Packages Needed
```R
install. packages(c("tidyverse", "lubridate", "scales"))
```
### Loading Packages Needed
```R
library(tidyverse)
library(lubridate)
library(scales)
```

#### Drawing a Line Chart
library(ggplot2)

```R
ggplot(kenya, aes(x = year, y = GDP)) +
  geom_line(linewidth = 1) +
  geom_point() +
  labs(
    title = "Kenya GDP per Capita",
    x = "Year",
    y = "GDP per Capita (USD)"
  ) +
  theme_minimal()
