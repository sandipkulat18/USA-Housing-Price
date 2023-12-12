# USA HOUSING- Data Science Model

Welcome to the "Exploring US Home Price Trends" project repository! In this project, we embark on a data-driven 
journey to understand the key factors influencing home prices in the United States over the past two decades.
By leveraging publicly available data and advanced data science techniques, our goal is to build a comprehensive
model that sheds light on the intricate relationship between various factors and home prices.

- [🔗 Data Cleaning](https://github.com/sandipkulat18/USA-Housing-Price/blob/main/Data%20Cleaning%20.ipynb): Details on data cleaning and preprocessing.
- [🔗 EDA_and_Feature_Engineering& model](https://github.com/sandipkulat18/USA-Housing-Price/blob/main/EDA%20analysis%20%26%20model_training.ipynb): Information about data relations and distributions.


Feel free to explore each section for a deeper understanding of the project.


## Libraries and Tools used:

- Programming Languages: Python
- Data Analysis Libraries: NumPy, pandas, matplotlib, seaborn
- Machine Learning Libraries: scikit-learn
- Data Visualization: Matplotlib, Seaborn
- Version Control: Git, GitHub
- Jupyter Notebooks for data exploration and analysis

## Data Collected

- Target (S&P/Case-Shiller U.S. National Home Price Index.)
- Population (Population includes resident population plus armed forces overseas.)
- Personal Income (Income that persons receive in return for their provision of labor, land, and capital used in
current production and the net current transfer payments that they receive from business and from government.)
- Gross Domestic Product (Featured measure of U.S. output, is the market value of the goods and services produced by labor and property located in the United States.)
- Unemployment Rate (The unemployment rate represents the number of unemployed as a percentage of the labor force. (16 years age or above))
- Mortgage Rate (A mortgage rate is the interest rate charged for a home loan.(Percentage))
- Employment- (Population Ratio (emratio))
- Building Construction issued permit in US (Total Units)
- Labor Force Participation Rate (The participation rate is the percentage of the population that is either working or actively looking for work.)
- Monthly Supply of New Houses in the United States (The monthly supply is the ratio of new houses for sale to new houses sold.)
- Housing starts (New Housing Project) (This is a measure of the number of units of new housing projects started in a given period.)
- Median Sales Price. (Median Sales Price of Houses Sold for the United States.(US Dollers))
- Producer Price Index -Cement Manufacturing
- Producer Price Index by Industry: Concrete Brick
- All Employees, Residential Building Construction (Thousands of Peoples)
(Construction employees in the construction sector include: Working supervisors, qualified craft workers, mechanics,
apprentices, helpers, laborers, and so forth, engaged in new work, alterations, demolition, repair, maintenance etc.)
- All Employees, Construction (Thousands of persons)
(Construction employees in the construction sector include: Working supervisors, qualified craft workers, mechanics,
apprentices, helpers, laborers, and so forth, engaged in new work, alterations, demolition, repair, maintenance.)
- Industrial Production: Cement
(The industrial production (IP) index measures the real output of all relevant establishments located in the United States)
- Homeownership Rate (Percentage)
(The homeownership rate is the proportion of households that is owner-occupied.)
- Personal Saving Rate (Percent)
(Personal saving as a percentage of disposable personal income (DPI), frequently referred to as "the personal
saving rate," is calculated as the ratio of personal saving to DPI. Personal income that is used either to provide
funds to capital markets or to invest in real assets such as residences.)
- New Privately-Owned Housing Construction Completed: (Total units in thousands)
- New Privately-Owned Housing Units Under Construction: Total Units in thousands

## Feature Selection

In our analysis, we identified several key features and their correlations with the target variable, represented by the S&P Case-Shiller Home Price Index.

| Feature                | Correlation with Home Price Index |
|------------------------|-----------------------------|
| target                 |  1.000000                     |
|MSPUS                   |  0.977394                     |
|PPI_Cement              |  0.959996                     |
|GDP                     |  0.956264                     |
|income                  |  0.949967                     |
|PPI_Concrete            |  0.936382                     |
|POP                     |  0.894797                     | 
|total_emp_cons          |  0.787229                     |
|new_private_hw_under    |  0.694883                     |
|all_Const_Emp           |  0.587502                     | 
|monthly_supply          |  0.242584                     |
|permit                  |  0.164303                     |
|RHORUSQ156N             |  0.098989                     |
|house_st                |  0.048265                     |
|new_private_house       |  0.003747                     |
|p_saving_rate           | -0.245506                    |
|IPI_Cement              |  -0.265593                    |
|unemployed_rate         |  -0.265985                    |
|emratio                 | -0.534276                    |
|mortgage_rate           |  -0.691159                   |
|labor_percent           |   -0.798548                |

The positive correlation values indicate a direct relationship with home prices, while negative values suggest an inverse relationship. Features with higher absolute correlation values have a larger impact on home prices.

## Model Selection and Cross-Validation

In this project, we employed the **Lasso regression** model due to indications of significant collinearity in the dataset. The Lasso regression model is known for its ability to handle collinearity by applying L1 regularization, which encourages sparsity in feature coefficients.

To optimize the Lasso model's performance and select the best regularization hyperparameter (alpha), we utilized **cross-validation**.

- Optimal alpha: **0.0034**.

The cross-validation process resulted in the following **R-squared** scores for different folds:
- Fold 1: 0.99511795
- Fold 2: 0.99630965
- Fold 3: 0.99531138
- Fold 4: 0.9958725
- Fold 5: 0.99598556


![image](https://github.com/sandipkulat18/USA-Housing-Price/assets/110375266/9f7ec29c-32ea-4dfd-8c42-255f188dfd9d)



- **mean R-squared** : **0.9957**
- **standard deviation R squared** : **0.0004**

## Best Features With non-zero Coefficients

Here are the features and their respective coefficients obtained from our Lasso regression model:

| Feature                | Coefficient  |
|------------------------|--------------|
|	all_Const_Emp	         | 14.815677    |
|	emratio	               |-24.005148    |
|	GDP	                   | 50.950283    |
|	RHORUSQ156N	           |  1.215961    |
| house_st	             |  -0.018994   |
|	income	               | -0.561788    |
|	IPI_Cement	           |   0.448277   |
|	labor_percent	         | 16.225860    |
|	monthly_supply	       | 4.142858     |
|	mortgage_rate	         | -4.772977    |
|	MSPUS	                 | 11.390086    |
|	new_private_house	     |  1.573229    |
|	new_private_hw_under	 | 7.037809     |
|	permit                 | 	0.266061    |
|   POP	                 | -25.808734   |
|	PPI_Cement	           |  1.301735    |  
|	PPI_Concrete	         | 4.707908     |
|	p_saving_rate	         | -2.458522    | 
|	total_emp_cons	       | -4.485266    | 
|	unemployed_rate	       |  -3.987282   |

These coefficients represent the impact of each feature on the prediction of home prices. Positive coefficients indicate a direct relationship with home prices, while negative coefficients suggest an inverse relationship.

## Features with zero Coefficient

In our analysis, some features in our Lasso regression model had coefficients of 0.0, indicating that they do not significantly impact the prediction of home prices. Here are the features with coefficients of 0.0:

|
These features do not have a significant impact on the prediction of home prices in our model.

## Sources

https://fred.stlouisfed.org/

