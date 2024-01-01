# Pichitapat Charoendhammatad - Portfolio
## About
Hello!  I'm Mint! I have a technical background and hold a Bachelor of Engineering in Chemical from Chulalongkorn university.

Complementing my academic background, I have pursued further education, completing a certificate program in, obtaining certifications in **IBM Data Analyst Professional, Machine Learning, and Business Analysis & Process Management.**

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
**Description**: The dataset is the applicants' profiles of those whose loan applications were previously accepted. There is a list of the amount of the loan, The number of payments on the loan, Interest Rate, loan grade, home ownership status, etc. This project making for proposing a new idea to help screen those applications from `'loan_status'`  data, which tell that the borrowers are `Fully paid` their loan or they haven't paid their installments in due time for a long period of time, `Charge off`.\
Data source: https://www.kaggle.com/faressayah/lending-club-loan-defaulters-prediction

The project includes the following steps: data loading, EDA (Exploratory Data Analysis) including data cleaning, filling missing values, and feature engineering, Then 
Training and testing a model, Evaluating model by Evaluation metrics, Interpret result.

**Skills**: Data cleaning, Data analysis, Data visualization, Machine learning model development, statistical factors.\
**Technology**: Python, Pandas, Numpy, Seaborn, Matplotlib,sklearn(LogisticRegression, DecisionTree, RandomForest, xgboost), Evaluation metrics (F1 score, confusion matrix, and Precision-Recall).\
**Results**: The number of payments on the loan and loan grade are the important features.

### 1.1 Investigate each feature
After finish data cleaning and fill missing value, the next step is to  investigate in both numeric and categorical. To find how much it is related to the target by using statistical measurements and visualization method. Then find out the features (Columns) which important to predict defaulters.
<img width="724" alt="image" src="https://github.com/pichitapat/Portfolio/assets/150525402/7c0b6959-9567-4634-98a0-ccfda9281427">
<img width="853" alt="image" src="https://github.com/pichitapat/Portfolio/assets/150525402/6bf519ac-c1ca-4f69-8ee3-46541eb7695a">
### 1.2 Prepare data
Prepare Dummies dataframe by join 'loan_status' column and deselect some features that not nessessary for prediction model, Then Spilt data set for Train and test. Here is parameter setup.
 ```
x_train, x_test, y_train, y_test = train_test_split(x, y, train_size=0.8, test_size=0.2, random_state = 123,stratify=df['loan_status'])
x_test, x_val, y_test, y_val = train_test_split(x_test, y_test, random_state = 123, test_size=0.5)
scaler = StandardScaler()
 ```
### 1.3 Train, evaluate, and fine-tune ML models
Develop 5 models to identify the best ML algorithm. The table below show all hyperparameters to fine-tune ML models \
|Model|ML algorithm|Hyperparameters|Note|     
|----|-----|-------|-----|    
|M1|Logistic regression model|C= (0.03125, 0.0625, 0.125, 1, 0.25, 0.5, 8, 1, 2)| Use all possible features|
|M2|Random forest model|min_samples_leaf: (1, 5, 10), min_samples_split: (2, 5, 10)| Use all possible features|
|M3|XGBClassifier|max_depth: (10, 15), max_leaves: (0, 5, 10)| Use all possible features|
|M4|XGBClassifier|max_depth: (10, 15), max_leaves: (0, 5, 10)| run the best model and hyperparameters from the above(the best model from M1,M2, and M3 is M3),apply a sampling-based technique for the imbalancedness|
|M5|XGBClassifier|max_depth=10, max_leaves=1| Customize the feature set by using any feature engineering techniques, run the best model and hyperparameters from the above (M4)|

Note for sampling-based technique for the imbalancedness :
 ```
over = SMOTE(sampling_strategy=0.3)
under = RandomUnderSampler(sampling_strategy=0.75)
steps = [('o', over), ('u', under)]
pipeline = Pipeline(steps=steps)
x_train_balance, y_train_balance = pipeline.fit_resample(x_train_scaled, y_train)
 ```

**Presented here is an exemple of the outcomes derived from M5, identified as the optimal model in our analysis.**
<img align="center" width="350" alt="image" src="https://github.com/pichitapat/Portfolio/assets/150525402/5d02c224-ca86-4306-bf04-6802e0e034bd" >


From confusion matrix above ,it means FN (False Negative) which is people who are predicted to be `Fully paid` but actually they are `Charged off` is 9.71% or 3,849 people and F1 score = 0.4250165892501659

### 1.4 Interpret results
The most important features (Top5) that derived from the best model (M5) are as follows:
|Feature|Important value|
|----|-----|
|new_sub_grade|0.259510|
|term_36|0.076317|
|mort_acc|0.038589|
|open_acc|0.033960|
|home_ownership_RENT|0.025937

### 1.4 Conclusion
* The predictive model, which identifies individuals likely to 'Charge off' their loan, yields more effective results when utilizing Resampling techniques
* The suitable algorithm for this project is **XGBClassifier**
* The first and second features are `sub_grade` and `term` which agree with our EDA earlier that found the two to have very different distributions.
* Applying this technique to be a strategy for future debt management planning. For instance, it could be used to implement approaches such as advance payment reminders and encouraging increased payment compliance.

### 1.5 Recommendations
* From the best model our F1-score is still pretty low. So, we can't actually use this model to predict charge-off applicants, but we might use this to shortlist who will has a chance instead.Additional techniques can be tried further such as better imputation and imbalance handling methods.
* Utilize clustering techniques to group borrowers, making it easier to tailor campaigns more precisely to the target groups

