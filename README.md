
# SyriaTel Customer Churn Rate
### by Salome Grasland 

## Business Understanding
SyriaTel, a telecommunications company, has approached us to help understand why customers are churning. Churning is an industry term used for when a customer chooses to leave or unsubscribe to the services provided by the company. Using the dataset provided we will investigate patterns contributing to churn rate. 

### The Problem
Currently, SyriaTel has a churn rate of 14.5% customers annually. An average churn rate for a good company is 5 to 7%, which means there is room for improvement. 

### The Solution
Using classification machine learning models we will identify what features contribute to the churn rate. Our model will focus on:
What is the relationship between churn and other features?
Which features increase the likelihood of churn?
#### Metric to use: Recall
A common data science question is should this model be more focused with precision or recall. Precision measures how precise the predictions are while recall measures what percentage of the classes we’re focused on are actually being captured by the model. For this model of primary concern is false negatives– predicting a customer will not churn when they do. Hence, recall is a better metric for this dataset. It is more costly for the company to predict that a customer would stay when they actually churn. By using recall more customer retention strategies can be implemented. It is more beneficial for the company to misidentify someone as ‘churning’ and use a strategy to keep them engaged rather than missing one who will churn and applying retention measures to have them continue using the services. 
## Methodology
The process for conducting our research and modeling will follow the iterative OSEMiN pipeline. This entails obtaining, scrubbing, exploring, modeling, and interpreting the data. 
## Obtaining the Data

- Importing libraries needed
- Opening the Data

This dataset has: 
- 21 columns 
- 3333 entries 
- Categorical and Continous Data 
## Scrubbing the Data
- Manage datatypes
- Resolve missing/duplicate values.
This dataset was pretty clean. There were no missing values or duplicates. 
## Exploring the Data
- Find patterns among the relationships of variables in the dataset. 
### Exploring the Target variable: 'Churn'

From the countplot below we can see that our target varibale is imablanced, this means that we will need to use SMOTE later. 
### Exploring Correlations
From this correlation map we can see that the charge columns are highly multicollinear with the minutes column. 

### Exploring categorical variables
From the pairplot we can see we have a few categorical variables:
- state
- international_plan
- voice_mail_plan
- churn

This will need to be enconded for modeling.

### Dropping unneccasary columns

For this project we are focused on the services and prices SyriaTel provides on the national level, so individual phone numbers and area codes are not necessary in this case. We also dropped the charge columns because they were multicollinear and added unnecessary noise to our dataset. 

### Converting categorical data

- state
- international_plan 
- voice_mail_plan 
- churn

We need to convert these so that we may intepret the data. 

## Modeling the Data
- Create baseline model 
- Iterate through different models 

### Define X and y

- Target variable (y): 'churn'
- Features (X): all othre columns

### Final Model on Test Data

The final model is a hypertuned XG Boost Model using scaled and resampled data. It has a recall score of 0.99 and a precision score of 1, this is excellent because our precision did not suffer due to prioritizing recall. Our model was able to predict 2133 out of 2137 churns and did not mislabel any customers that did not leave. The train and test score were both 1 meaning that our model performs well on real world conditions.

## Interpreting the Data
- Identify insights 
- Visualize findings

### Feature Importance on XG Model Boost

By using scikit learns feature importance we can see what variables most impacted customer churn rate. 

### Top Feature Visualization 

To help us understand how our most important feautres impact churn rates lets visualize them. The three features that had the highest impact on churn rate were:   
- ‘International_plan’: Does the customer have an international plan or not    
- ‘Customer_serivce_calls’: How many calls has the CST made to customer service   
- ‘Total_day_minutes’: How many minutes a day is this CST on the phone 
 
#### Churn by Number of Customer Service Calls 
On average customers who churned made 2.2 customer service calls, with 4 calls being the point where more than half of customers churned. Perhaps in the future customers who are calling for the 3rd time can be channeled to more senior customer service agents. This kernel also looked at the most important features in regard to customer service calls and found that ‘international_plan’, ‘total_day_minutes”, and ‘total_intl_calls’ were the top 3 variables. It seems as if customers who need to use the companies international services are more likely to churn. The company should consider allocating more resources to their international plans in order to retain customers. 

#### Churn by Total Day Minutes

After about 275 total day minutes churn becomes dominant. 

## Conclusion and Further Work 

Our model was able to predict 2133 out of 2137 churns and did not mislabel any customers that did not leave. Using the model to identify customers that will churn can help SyriaTel reach their churn rate of 5 to 7%. 


### Recommendations 
The recommendation we make to SyriaTel is:
- Create an international team, whose focus is dealing with customers using international plans 
- Incentivize resolving calls in 1 to 2 calls 
- Funnel customers calling in for the 3rd time to senior agents who can provide the best help 
- Audit high use customers 
- Improve customer service training on international services

### Further Work
SyriaTel could benefit from collecting not just state by state data, but also country by country data. It would be interesting to see if international plans being used in certain countries are more likely to churn. SyriaTel could then allocate funds based on countries that generate the most profits for international plans. SyriaTel could also look at countries that have high churn rates to see what competitors offer that SyriaTel does not. 

## For More Information
For additional info, contact Salome Grasland at salome.grasland@ncf.edu

