# Data Science Salary Estimator: Project Overview

* Created a tool that estimates data science salaries (Mean Absolute Error ~ $ 11K) to help data scientists negotiate their salaries when the get a job.
* Used the dataset from a similar project [DataSet](https://raw.githubusercontent.com/PlayingNumbers/ds_salary_proj/data_cleaning/glassdoor_jobs.csv).
* Engineeredd features from the text of each job description to quantify the value companies put on different tools like python, aws etc.
* Optimized Linear, Lasso and Random Forest Regressors using Grid search.

## Code and Resources Used

**Python Version:** 3.7

**Packages:** numpy, pandas, sklearn, seaborn, matplotlib, pickle

**Data Set:** [DataSet](https://raw.githubusercontent.com/PlayingNumbers/ds_salary_proj/data_cleaning/glassdoor_jobs.csv)

**Popular Data Science tools list:** [Top Data Science Tools](https://www.kdnuggets.com/2019/05/poll-top-data-science-machine-learning-platforms.html#:~:text=Python%20leads%20the%2011%20top%20Data%20Science,Learning%20platforms%3A%20Trends%20and%20Analysis&text=Python%20continues%20to%20lead%20the,By%20Gregory%20Piatetsky%2C%20KDnuggets.)

**Reference:** [Ken Jee Youtube](https://www.youtube.com/playlist?list=PL2zq7klxX5ASFejJj80ob9ZAnBHdz5O1t)

## Project Walk-Through

### Data Wrangling

I had to clean the data so that it was usable for the model. I made the following changes and created the following variables:

* Parsed numeric data out of the salary
* Made columns for employer provided salary and hourly wages
* Removed the rows without salaries
* Parsed rating out of company text
* Made a new column for job state
* Transformed year into age of company
* Made columns for the tools and skills listed in the job description:
  + Python
  + R
  + Excel
  + Anaconda
  + RapidMiner
  + SQL
  + Tensorflow
  + Tableau
  + Spark
  + AWS
 * Column for simplified job title
 * Column for description length
 
## Exploratory Data Analysis 

I looked at the distributions of the data and the value counts for the various categorical variables. Below are few highlights from pivot tables.

![Average Salary for different Jobs](https://github.com/MrLuciferM/DataScience_salary_proj/blob/master/pivot_table_jobtitle.jpg) ![Heatmap for correlation between differnt features](https://github.com/MrLuciferM/DataScience_salary_proj/blob/master/heatmap.png)
![Jobs in different States](https://github.com/MrLuciferM/DataScience_salary_proj/blob/master/barplot_state.png)

## Model Building

First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.

I tried three different models and evaluated them using Mean Absolute Error. I chose it because it is relatively easy to interpret and outliers are not particularly bad in for this type of model.

I tried three different models:

* **Multiple Linear Regression** - Baseline of the model
* **Lasso Regression** - Because of the sparse data from the many categorical variables, I thought a normalized regression like lasso would be effective.
* **Random Forest Regressor** - Again, with the sparsity associated with the data, I thought that this would be a good fit.

## Model Performance

The Random Forest model far outperformed the other approaches on the test and validation sets.

* **Random Forest**: MAE = 11.29
* **Linear Regression**: MAE = 18.76
* **Lasso Regression**: MAE = 19.40
