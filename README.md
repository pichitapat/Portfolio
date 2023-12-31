# Pichitapat Charoendhammatad - Portfolio
## About
Hello!  I'm Mint! I have a technical background and hold a Bachelor of Engineering in Chemical from Chulalongkorn university.

Complementing my academic background, I have pursued further education, completing a certificate program in, obtaining certifications in IBM Data Analyst Professional, Machine Learning, and Business Analysis & Process Management.

In this repository, you will see a topic about my study project that demonstrate the following, but not limited to the following skills: 
Data gathering with APIs, Data wrangling, Data exploration, Machine Learning model development, Statistical analysis, Data visualization, Presentation skills, etc.

My Resume in [Resume](Pichitapat_Resume.pdf) \
Linkedin: [My Linkedin](www.linkedin.com/in/pichitapat-charoendhammatad-9b2949296)
## Table of Content
* **About**
* **Projects**
  1. [Credit Approval](#Project-1---Credit-Approval)
  2. Developer Survey Analytics
## Projects
### Project 1 - Credit Approval 
**Code**: [Credit_card_approval.ipynb](Credit_card_approval.ipynb) \
**Description**: The dataset is the applicants' profiles of those whose loan applications were previously accepted. There is a list of the amount of the loan, The number of payments on the loan, Interest Rate, loan grade, home ownership status, etc.This project making for proposing a new idea to help screen those applications from ` 'loan_status'`  data, which tell that the borrowers are fully paid their loan or they haven't paid their installments in due time for a long period of time.\
Data source: https://www.kaggle.com/faressayah/lending-club-loan-defaulters-prediction

The project includes the following steps: data loading, EDA (Exploratory Data Analysis) including data cleaning, filling missing values, and feature engineering, measuring statistical factors, Interpret result.

**Skills**: data cleaning, data analysis, descriptive statistics, central limit theorem, hypothesis testing, data visualization. \
**Technology**: Python, Pandas, Numpy, Seaborn, Matplotlib,sklearn.\
Results: The number of payments on the loan and loan grade are the important features.
### 1.1 Investigate each feature
After finish data cleaning and fill missing value, the next step is to  investigate in both numeric and categorical. To find how much it is related to the target by using statistical measurements and visualization method. Then find out the features which important to predict defaulters.
<img width="724" alt="image" src="https://github.com/pichitapat/Portfolio/assets/150525402/7c0b6959-9567-4634-98a0-ccfda9281427">
<img width="853" alt="image" src="https://github.com/pichitapat/Portfolio/assets/150525402/6bf519ac-c1ca-4f69-8ee3-46541eb7695a">
### 1.2 Prepare data
Prepare Dummies dataframe by join 'loan_status' column and deselect some column that not nessessary for prediction model
