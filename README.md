# Data Science Salary Estimator: Project Overview 
* Created a tool that estimates data science salaries (MAE ~ $ 11K) to help data scientists negotiate their income when they get a job.
* Scraped over 1000 job descriptions from glassdoor using python and selenium.
* Engineered features from the text of each job description to quantify the value companies put on python, tableau, tensorflow, pytorch, excel, aws, and spark. 
* Optimized Linear, Lasso, Xgboost, and Random Forest Regressors using GridsearchCV to reach the best model. 


## Code and Resources Used 
**Python Version:** 3.7  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn, selenium, pickle.    
**Scraper Github:** https://github.com/arapfaik/scraping-glassdoor-selenium 

## Step 1: Web Scraping
Tweaked the web scraper github repo (above) to scrape 1000 job postings from glassdoor.com. With each job, we got the following:
*	Job title
*	Salary Estimate
*	Job Description
*	Rating
*	Company 
*	Location
*	Company Headquarters 
*	Company Size
*	Company Founded Date
*	Type of Ownership 
*	Industry
*	Sector
*	Revenue
*	Competitors 

## Step 2: Data Cleaning
After scraping the data, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

*	Parsed numeric data out of salary 
*	Made columns for employer provided salary and hourly wages 
*	Removed rows without salary 
*	Parsed rating out of company text 
*	Made a new column for company state 
*	Added a column for if the job was at the company’s headquarters 
*	Transformed founded date into age of company 
*	Made columns for if different skills were listed in the job description:
    * Python  
    * R  
    * Excel  
    * AWS  
    * Spark 
    * Tensorflow & PyTorch
*	Column for simplified job title and Seniority 
*	Column for description length 

## Step 3: EDA
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the Exploratory Data Analysis. 

![alt text](https://github.com/vikasbhadoria69/Data-Science-Project-from-scratch-/blob/master/EDA_Graphs/Average_salary_for_each_domain.png)
![alt text](https://github.com/vikasbhadoria69/Data-Science-Project-from-scratch-/blob/master/EDA_Graphs/Jobs_per_domain.png)
![alt text](https://github.com/vikasbhadoria69/Data-Science-Project-from-scratch-/blob/master/EDA_Graphs/Most_jobs_per_location.png)
![alt text](https://github.com/vikasbhadoria69/Data-Science-Project-from-scratch-/blob/master/EDA_Graphs/Type_o_company_ownership.png)
![alt text](https://github.com/vikasbhadoria69/Data-Science-Project-from-scratch-/blob/master/EDA_Graphs/WordCloud.png)

## Step 4: Model Building 

First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.   

I tried three different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.   

I tried three different models:
*	**Multiple Linear Regression** – Baseline for the model
*	**Lasso Regression** – Because of the sparse data from the many categorical variables, I thought a normalized regression like lasso would be effective.
*  **XgBoost** - It is easy to get a lower testing error compared to linear models. Boosting takes slower steps, making predictors sequentially instead of independently.
*	**Random Forest** – Again, with the sparsity associated with the data, I thought that this would be a good fit. 

## Model performance
The Random Forest model far outperformed the other approaches on the test and validation sets.I then used GridsearchCV to obtain the best parameters for Random Forest.
*	**Random Forest** : MAE = 11.023
*	**XgBoost** : MAE = 12.936
*	**Linear Regression**: MAE = 18.855
*	**Lasso Regression**: MAE = 19.665
