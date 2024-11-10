# SQL and Power BI Bike Store Pricing Recommendation Data Analysis Project 

## Objective
The Project is to develop a dashboard for the "Toman Bike Store" to display KPIs for informed decision-making and to give <ins>recommendation if the store can raise their prices</ins> for the following year.

## Requirements
- Hourly Revenue Analysis
- Profit and Revenue Trends
- Seasonal Revenue
- Rider Demographics

## Dataset
Dataset contains three CSV Files [bike_share_yr_0](https://github.com/AkarshGM/SQL-and-Power-BI-Bike-shop-Project/blob/main/bike_share_yr_0.csv), [bike_share_yr_1](https://github.com/AkarshGM/SQL-and-Power-BI-Bike-shop-Project/blob/main/bike_share_yr_1.csv), [cost_table](https://github.com/AkarshGM/SQL-and-Power-BI-Bike-shop-Project/blob/main/cost_table.csv) and I have used SQL Server to join these tables together and then connect it to Power BI.
```sql
WITH cte as (
SELECT * FROM bike_share_yr_0
UNION ALL
SELECT * FROM bike_share_yr_1)


SELECT 
	dteday,
	season,
	a.yr,
	weekday,
	hr,
	rider_type,
	riders,
	price,
	COGS,
	riders*price as revenue,
	riders*price - COGS*riders as profit
FROM cte a
LEFT JOIN cost_table b
ON a.yr = b.yr
```
Created two new columns Revenue and Profit for Analysis.

## Dashboard
Connected SQL Server to Power BI and developed an Interactive Dashboard to analyse Hourly Revenue Analysis, Profit-Revenue Trends, Seasonal Revenue and Rider Demographics. 

![Dashboard](https://github.com/AkarshGM/SQL-and-Power-BI-Bike-shop-Project/blob/main/Power%20BI%20Dashboard.png)

## Interpretation
Using the following data to check if the store can increase its price.

![DATA](https://github.com/AkarshGM/SQL-and-Power-BI-Bike-shop-Project/blob/main/DATA.png)

- It seems that there was 25% increase in price (from $3.99 to $4.99) from the year 2021 to 2022 and there was a giant jump in revenue.
- There is aslo 64% increase in demand. [(2049576-1243103)/1243103*100)]
- Price Elasticity is 2.56 (64%/25%) and hence we can increase the price conservatively.

## Recommendation
- **Conservative Increase**: Considering the substantial increase last year, a more conservative increase might be prudent to avoid hitting a price ceiling where demand starts to drop. An increase in the range of 10-15% could test the market's response without risking a significant loss of customers.
- **Price Setting**:
 	- If the price in 2022 was $4.99, a 10% increase would make the new price about $5.49
    - A 15% increase would set the price at approximately $5.74

## Recommended Strategy
- **Market Analysis**: Conduct further market research to understand customer satisfaction, potential competitive changes and the overall economic environment. This can guide whether leaning towards the lower or higher end of the suggested increase.
- **Segmented Pricing Strategy**: Consider different pricing for casual vs registered users, as they may have different price sensitivities.
- **Monitor and Adjust**: Implement the new prices but to be ready to adjust based on immediate customer feedback and sales data. Monitoring closely will allow to fine-tune pricing strategy without committing fully to a price that might turn out to be too high.

[Link to download Live Dashboard Power BI File](https://github.com/AkarshGM/SQL-and-Power-BI-Bike-shop-Project/blob/main/Bike%20data%20Power%20BI%20Project.pbix)


