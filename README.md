# Adidas-Sales

The Adidas Sales dataset is originally found in [Dataworld](https://data.world/stellabigail/adidas-us-sales-datasets) by Stella Abigail. A registration is needed to access the dataset. Alternatively, you may access the dataset via [Kaggle](https://www.kaggle.com/datasets/heemalichaudhari/adidas-sales-dataset). You may also find this `Adidas US Sales.csv` in the Dataset/clean directory.

## Motivation
Effective forecasting of demand ensures optimal production of products and minimise inventory costs through storing excessing products produced. Furthermore, with the less-promising macroeconomic outlook and post-covid-19 recovery,  retailers need to have high operating margin to ensure they have enough revenues buffer to tide through the less-promising outlook for the next 2 years. This projects seeks to idenify
1. The factors affecting the amount of units sold.
2. The factors affecting the operating margin of each retail.

## Preliminary Preprocessing
1. Remove the $, commas and % signs from the datasets
2. Convert those columns into numerical columns

## Exploratory Data Analysis (EDA)
The EDA can be accessed by downloading the `2) EDA.html` file in the `EDA and preprocessing` folder.
We will seek to explore the
1. Monthly variation of Adidas sales of each product by gender in 2020 and 2021.
2. The variation of Adidas sales by different US retailers in 2020 and 2021.
3. The variation of Adidas sales by different Sales method in 2020 and 2021.
4. The variation of Adidas sales by different regions in 2020 and 2021.
5. The distribution of operating margin by US retailers in 2020 and 2021.
6. The distribution of Profit from Adidas Sales by US retailers in 2020 and 2021.
7. The geospatial variation of Adidas Sales by States in USA in 2020 and 2021.

## General preprocessing before Modelling
1. Remove the `Operating Profit` and `Total Sales` columns to prevent data leakage.
2. Perform the necessary encoding on the respective variables.

#### Units Sold Prediction
1. Drop the `Operating Margin` column in the dataset 
2. Perform the splitting into training and testing datasets.
3. Perform Mutual Information and the correlation test on the numerical variables.
4. Perform Mutual Information on the categorical variables.
5. Remove variables with 0 for mutual information
6. Train them with Random forest, XGBoost, LGBM, ELastic Net and CatBoost regression models.

#### Operating Margin Prediction
1. Perform the splitting into training and testing datasets.
2. Perform Mutual Information and the correlation test on the numerical variables.
3. Perform Mutual Information on the categorical variables. Remove variables with 0 for mutual information
4. Remove varaibles with low Mutual information and Chi square test.
5. Train them with Random forest, XGBoost, LGBM, ELastic Net and CatBoost regression models.

## Evaluation Criterions
* Root Mean Squared Error(RMSE) is used to evaluate the performance of the regression models
* Since there are 50 to 60 columns of training data, an adjusted R-score is used as the secondary criteria of performance for the regression models.

## Adidas US Sales Dataset Description
The dataset of interest is adidas_sales_new.csv since it is easily usable for EDA and modelling.
#### adidas_sales_new.csv
| Column Name | Description |
| --- | --- |
| ``(string) | unique identifier of transactional order from port inbound to final destination. Primary key of data set. |
| `Retailer`(string) | Name of the US retailer which sells Adidas products |
| `Retailer ID`(string) | Unique Identification number for each US retailer |
| `Invoice Date`(string) | Date of transaction made |
| `Year`(integer) | Year of the transaction made |
| `Month`(integer) | Month of the transaction made |
| `Day`(integer) | Day of the transaction made |
| `Region`(string) | US region location of the retail |
| `State`(string) | Name of the US states |
| `City`(string) | Name of the city in that particular US states|
| `Sales Method`(string) | Purchase methods of the Adidas products|
| `Gender`(string) | Gender of the Adidas products purchased|
| `Product`(string) | Product of the Adidas products purchased|
| `Price per Unit`(string) | Price per unit of the Adidas product|
| `Units Sold`(string) | Quantity of Adidas product purchased|
| `Total Sales`(Integer) | Total Revenue generated from Adidas products|
| `Operating Margin`(Integer) | financial metric of the specific retail that measures the profitability of a company by showing the percentage of revenue that remains after deducting operating expenses such as wages, rent, and supplies.|
| `Operating Profit`(Integer) | A product of `Operating Margin` column with the `Total Sales` Column|