# **ATLIQ HARDWARE SALES INSIGHTS WITH MYSQL AND POWERBI**
AtliQ Hardware is a company which supplies computer hardware and peripherals to many of clients .
AtliQ Hardware head office is situated in Delhi, India and they have many regional office through out the India.

Sales director for this company is facing a lot of challenges is this the market is growing dynamically and sales director is facing issue in terms of tracking the sales 
in this dynamical growth market
and he is having issues with growth of this bussiness, as overall sales was declining. He has regional manager for North India, South and Central India. 
Whenever he wants to get insights of thses region he would call these people and on the phone regional manager give some insights to him that this was the sales last quarter 
and we are going to grow by this much in the next quarter.

The problem was that all these thing happening is verbal and these was no proof with facts that how his business is affected and which made him frustraed 
as he can see that overall sales is declining but when he can ask regional manager, he is not getting complete picture of this bussiness and when he 
and this AtliQ hardware is big business. so to see insights clearly. and he will get proper insights anbd can take data driven decision to increase sales of hos company.
All he wants is a simple data visualization tool which he can access on daily basis. By using such tools and technology one can make data driven decisiions 
which helps to increase the sales of the company.
So, In this projects we will help a company make its own sales related dashboard using power BI.I get data from Mysql .

## **Data Exploration**
### + Project Planning using AIMS Grid -
It is a project management tool which consists of four components-

1.Purpose - (What to do exactly)

2.Stackholder - (Who will be involved)

3.End result - (What do you want to achieve)

4.Success Criteria - (Cost optimization and time save)

#### **AIMS Grid** -

1. **Purpose** :- To unlock sales insights that are not visible before for the sales them for decision support and automate them to reduced manual time spent in data gathering.

2. **Stakeholders** :-

               a. Sales Director


               b.Marketing Team


              c.Customer Service Team


              d.Data and Analytics Team


              e.IT


3. **End result** :- An automated dashboard providing quick and latest sights in order to support Data driven decision making.

4. **Success Criteria** :-

Dahboard uncovering sales order insights with latest data available
Sales team able to take better decisions and prove 10% cost saving of total spend.
Sales analysis stop data gathering manually in order to save 20% business time and reinvest it value added activity.

##### **Data Analysis using SQL**
SQL database dump is in db_dump.sql file above. Download db_dump.sql file to your local computer
Now,

Importing Data to MySQL workbench
After importing data , we go through with some queries to cleaning up of data.

we have certain unnecessary values in market table to find use below query

          SELECT * FROM market;

Similarly , we can check that transacation table we can see that ceratin negative value in amount which is not possible.
and we can see that certain transactions are in USD. Hence, filtration of that is also needed by converting into INR.
i.e  

        SELECT * FROM sales.transactions;

###### EXTRACT , TRANSFORM ND LOAD

            In this step we connect MYSQL Database to powerbi desktop.
  NOW , With the help of powerquery editor we
 Perform filtration in market’s table: 
 In the tables perform when we click on the transform data option, we are directed to Power query editor. 
 Power query editor is where we perform out ETL.and then we can perform data transformation 
 i.e. Data Cleaning, Data Wrangling, Data Munging. we need to filter the rows where the values are null and filtering the data and deselecting the blank option.
 In the table perform when we check the query in the MySQL to filter some negative values and also 0 values that appears in the table, 
the desired output is received.and we will perform the similar filtration in PowerBI. 
we have deselecting the values, don’t want in the table. 
The result after filtration. the zero values represent some garbage values which is not possible so we need to clean that data.

Convert USD into INR in the transaction’s table: the AtliQ Hardware only works in India so the USD values are not possible. we need to convert those USD values into INR by using some formulas. Add new column - Conditional column - normalized currency where sales amount will be in INR

#######DAX

In power query editore finding the total values having USD as currency.

 `=Table.AddColumn(#"Filtered Rows", "norm_sales_amount",each if [currency] = "USD" then [sales_amount]*75 else [sales_amount]
 using this correct formula of the conversion,and converted the USD currency into INR.

 This is our Relationship of table -
 
 ![relationship](https://github.com/Mandarsir24/ATLIQ-Hardware-Sales-insights-/assets/152494714/32f37865-5eb8-4ca4-93a7-df7b6f49d3b8)

 DASHBOARD - 
 ![DASHBOARD 1](https://github.com/Mandarsir24/ATLIQ-Hardware-Sales-insights-/assets/152494714/424ad66a-3e70-4547-a5c5-d8ec0c9bf3ca)















