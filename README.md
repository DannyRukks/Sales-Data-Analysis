# Sales-Data-Analysis: MeriSkill Internship Project
# Introduction
MeriSkill Internship is designed to provide a unique chance to learn and actively contribute to the organization's data-driven initiatives. It opens up the opportunity to gain invaluable hands-on experience in various facets of data analysis and interpretation. This includes tasks such as data collection, analysis, visualization, and drawing meaningful insights.

This project involved performing data wrangling on a  historic sales dataset and creating visuals with the aim of generating insights and trends that could informed business decisions. The dataset consists of 13621 records and 11 features stored in a Microsoft Excel File. The dataset comprises of numerical and categorical columns such as order id, product, quantity ordered, price, order date, purchase address, month, sales, city and hour.It contains several products that were sold in different cities at different sales price in the year 2019 and 2020 and each product has an order id.
# Objectives
- perform data cleaning of the dataset
- Data Modelling
- Analyze the dataset
- Creating visuals and dashboard to uncover insights and trends that could informed business decisions.
- Provide recommendations
# Tools used
- Excel - Data Source and Inspection
- Power BI - Creating Reports
- Power Query - Data Cleaning and Data Analysis
# Data Cleaning/preparation
The following tasks were performed in the data cleaning and preparation phase
- Data loading and inspection
- Handling missing and null values
- Data Cleaning and formatting
- Validating columns data types
# Data Modelling and Visualization
Three tables were created in this project. These are the sales, products and dates tables. The sales table is the fact table while the dates and products tables are the dimension tables. A star schema data model was created as shown below. A one to many relationship was established between the dimension and fact tables.

![Data Model View](https://github.com/DannyRukks/Sales-Data-Analysis/assets/97890440/96bfdf15-d76a-4f32-89e2-9bd8eaabc6e3)

The dataset was explored and analyzed. The following measures were created and metrics that helped in generating insight and discovering sales trends were calculated as shown below:
```
Total Sales = SUM(Sales[Sales])
```
```
Total Quantity Ordered = SUM(Sales[Quantity Ordered])
```
```
Total Products = DISTINCTCOUNT(Sales[Product])
```
```
Top 5 Products with Highest Sales = SUMX(
    ADDCOLUMNS(
        Products,
        "Ranks",
        RANKX(ALL(Products), [Total Sales],,DESC)),
        IF([Ranks] <= 5, [Total Sales], BLANK()))
```
```
Top 5 Products with Highest Quantity Ordered = SUMX(
    ADDCOLUMNS(
        Products,
        "Rankings",
        RANKX(ALL(Products), [Total Quantity Ordered],,DESC)),
        IF([Rankings] <= 5, [Total Quantity Ordered], BLANK()))
```
```
Previous Month Sales = CALCULATE(
    [Total Sales],
   DATEADD(Dates[Date], -1, MONTH))
```
```
Monthly Sales% Change = IF(
    [Previous Month Sales] = 0, 1,
    IF(ISFILTERED(Dates[MonthName]),
    DIVIDE([Total Sales] - [Previous Month Sales], [Previous Month Sales]), 0))
```
These measures were then used to generate interactive visualizations, metrics and dashboard as shown below:

