# Overview
After a quick data exploration in MySQL, here are some initial findings:

- The database contains 5 tables: customers, date, markets, products, and transactions;
- There are 17 markets, 279 products, and 38 customers;
- The observation period is from january 2018 to june 2020;
- The total revenue in 2020 was $ 142,23 Mi, 42% less than 2019, which was $ 336,45 Mi;
- Most of the transactions data are in INR currency, but we have 4 records in U$ currency.
- And we got Paris and New York on the “sales markets” table. We’re going to deal with it in the ETL process.

# ETL (Extract, Transform, Load)
Once I know the basic features of the data I have to work with, I imported the MySQL database into Power BI to do the necessary transformations and end up with a simple, reliable, and useful dashboard.

*Data Modeling Step* <br/>
We got five tables and we need to ensure that the tables are correctly connected. <br/>

![Data Modelling](https://github.com/aman-thapa/Sales-Insights-bi/blob/main/Images/Data%20Modelling.JPG)

**[sales transactions]** — main table
TABLES CONNECTED
- sales customers > connected by “customer_code” column;
- sales date> connected by “date” column;
- sales products > connected by “product_code” column;
- sales markets > connected by “market_code” column.

*Cleaning and adding new column*
- The “sales_amount” column has -1 and 0 values. 
I removed them in this case so we can see only the actual sales numbers on the dashboard (sometimes “0” means promotional sales and giveaways, but to know that, we should have further information, which is not the case of this project).
- I find out that the “currency” column (sales transactions table) have 4 USD currency values, 2 of them with hidden characters, so i had to include an argument into the conditional formula, in order to create a new column called “norm_sales_amount”, where it converts the USD currency value into INR currency value.
