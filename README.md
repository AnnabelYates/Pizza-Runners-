# Pizza Runners Data Cleaning and Exploratory Analysis

Using SQL, I cleaned a database and performed an exploratory data analysis for a mobile pizza delivery service. I worked on [Data with Danny's case study #2](https://8weeksqlchallenge.com/case-study-2/) to practice my SQL skills. Big thanks to Data with Danny for creating such an amazing opportunity!

## Executive Summary:

Using MYSQL Workbench, I created a schema with 6 tables uploaded from CVC files. Using SQL, I 

From the analysis, I discovered that. I presented the following business recommendations to : 

1) 

2) 

3) 

## Business Problem:



#### Can you identify key details about ?

## Methodology:

1) Using MYSQL Workbench, create a new schema and 6 associated tables using the values provided.

2) Clean and prepare database for analysis. 
   
3) Use SQL queries to answer a series of questions

## Skills: 

#### SQL:

creating schemas and data tables, basic queries, data cleaning

## Results and Business Recommendations:
### 1) Setting Up the Database: 

I created a new schema in MYSQL Workbench called pizza_runners. Then, I added the 6 provided data tables using Table Data Import Wizard and CVC files. I allowed the program to auto select the data types for each column so I could practice data cleaning. 

### 2) Data Cleaning and Preparations:

#### Null and Missing Values:

- To resolve missing and null values in the customer_orders table, I created the 2 following queries which replace empty values and NULL in the exclusions column with none. 

UPDATE customer_orders
SET exclusions = 'none'
WHERE exclusions IS NULL; 

UPDATE customer_orders
SET exclusions = 'none'
WHERE TRIM(exclusions) = ''; 

- I repeated this process for the extras column in the customer_orders. Additionally, I changed a value of NaN to none. 

UPDATE customer_orders
SET extras = 'none'
WHERE extras IS NULL;

UPDATE customer_orders
SET extras = 'none'
WHERE TRIM(extras) = ''; 

UPDATE customer_orders
SET extras = 'none'
WHERE extras = 'NaN';

- In the runner_orders table, in the pickup_time, distance and duration columns, I substituted NaN for null for clarity.

UPDATE runner_orders
SET pickup_time = 'NaN'
WHERE pickup_time IS NULL;

UPDATE runner_orders
SET distance = 'NaN'
WHERE distance IS NULL;

UPDATE runner_orders
SET duration = 'NaN'
WHERE duration IS NULL;

- In the runner_orders table, in the cancellation column, I substituted null, empty and NaN values for no to make it clearer that there was no cancellation.

UPDATE runner_orders
SET cancellation = 'no'
WHERE cancellation IS NULL;

UPDATE runner_orders
SET cancellation = 'no'
WHERE cancellation = 'NaN';

UPDATE runner_orders
SET cancellation = 'no'
WHERE TRIM(cancellation) = '';

#### Consistency and Formatting: 

- As a minor formatting fix to maintain consistency throughout the data schema, I changed the topping_name column values in the pizza_toppings table to be all lower case. 

UPDATE pizza_toppings
SET topping_name = LOWER(topping_name);

- I simplified the reasons for cancellation in runner_orders to restaurant and customer. 

UPDATE runner_orders
SET cancellation = 'restaurant'
WHERE cancellation =  'Restaurant Cancellation';

UPDATE runner_orders
SET cancellation = 'customer'
WHERE cancellation =  'Customer Cancellation';

### Case Study Questions: 

### Business Recommendations: 

## Next Steps: 
