# SQL and Power BI Bike Store Data Analysis Project 

## Objective
The Project is to develop a dashboard for the "Toman Bike Store" to display KPIs for informed decision-making and to give recommendation if the store can raise their prices for the following year.

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
