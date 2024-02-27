# Sales-Data-Analysis: MeriSkill Internship Project
# Introduction
MeriSkill Internship is designed to provide a unique chance to learn and actively contribute to the organization's data-driven initiatives. It opens up the opportunity to gain invaluable hands-on experience in various facets of data analysis and interpretation. This includes tasks such as data collection, analysis, visualization, and drawing meaningful insights.

This project involved performing data wrangling on a  historic sales dataset and creating visuals with the aim of generating insights and trends that could informed business decisions. The dataset consists of 13621 records and 11 features stored in a Microsoft Excel File. The dataset comprises of numerical and categorical columns such as order id, product, quantity ordered, price, order date, purchase address, month, sales, city and hour.It contains several products that were sold in different cities at different sales price in the year 2019 and 2020 and each product has an order id.
# Objectives
- perform data cleaning of the dataset
- Data Modelling
- Analyze the dataset
- Create visuals and dashboard to uncover insights and trends that could informed business decisions.
- Provide recommendations
# Tools used
- Excel - Data Source and Inspection
- Power BI - Creating Reports
- Power Query - Data Cleaning and Data Analysis
# Data Cleaning/Preparation
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

![Sales Dashboard1](https://github.com/DannyRukks/Sales-Data-Analysis/assets/97890440/7d60e37f-b412-4c0f-8ad2-72d73e5ca720)

# Insights
Here are some of the basic insights from the data analysis
- The total quantity ordered is 209079
- There are 19 different product that were sold
- Total of $34.49 million of sales were generated
- The top five products with high sales generated are Macbook pro laptop, iphone, thinkpad laptop, google phone and 27in 4K gaming monitor
- The top five products with the most quantity ordered are AAA batteries, AA batteries, USB-C Charging cable, lightning charging cable and wired headphones.
- Cities with the highest sales are Sales are San Francisco, Los Angeles, New York City, Boston and Atlanta.
- The month of December 2019 generated the highest sales revenue of about $4.613 million
# Recommendations
- Invest more on products with high sales
- Create awareness and enlightenment to be made in cities where sales are low.
- Strategize to boost sale of product with low sales
- Boost productivity in months where sales are highly generated
- Develop strategies to sustain sales in cities with high revenue
# Conclusion
Specific decisions and actions can now be taken with the aid of the provided recommendations and calculated KPI metrics in order to boost productivity and sales revenues. Click [here](https://drive.google.com/file/d/1wnwzgJfT71PcWEPMVdGE_uAN8ZEJa_kA/view?usp=sharing) to access the dashoard for interactivity.

# Thanks
