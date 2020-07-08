# Data Science Salary Estimator: Project Overview 
* Created a tool that estimates data science salaries (MAE ~ $ 11K) to help data scientists negotiate their income when they get a job.
* Scraped over 1000 job descriptions from glassdoor using python and selenium.
* Engineered features from the text of each job description to quantify the value companies put on python, tableau, tensorflow, pytorch, excel, aws, and spark. 
* Optimized Linear, Lasso, Xgboost, and Random Forest Regressors using GridsearchCV to reach the best model. 


## Code and Resources Used 
**Python Version:** 3.7  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn, selenium, pickle.    
**Scraper Github:** https://github.com/arapfaik/scraping-glassdoor-selenium 

## Web Scraping
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

## Data Cleaning
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

## EDA
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the Exploratory Data Analysis. 

![alt text](https://github.com/vikasbhadoria69/Data-Science-Project-from-scratch-/blob/master/EDA_Graphs/Average_salary_for_each_domain.png)
![alt text](https://github.com/vikasbhadoria69/Data-Science-Project-from-scratch-/blob/master/EDA_Graphs/Feature_Correlations.png)
![alt text](https://github.com/vikasbhadoria69/Data-Science-Project-from-scratch-/blob/master/EDA_Graphs/Jobs_per_domain.png)
![alt text](https://github.com/vikasbhadoria69/Data-Science-Project-from-scratch-/blob/master/EDA_Graphs/Most_jobs_per_location.png)
![alt text](https://github.com/vikasbhadoria69/Data-Science-Project-from-scratch-/blob/master/EDA_Graphs/Type_o_company_ownership.png)
![alt text](https://github.com/vikasbhadoria69/Data-Science-Project-from-scratch-/blob/master/EDA_Graphs/WordCloud_based_on_JobDescription.png)
