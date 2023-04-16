# Credit-Card-Fraud-Detection
Analysis of different machine learning algorithms for credit card fraud detection

# Importing Dependencies 
Importing **numpy** and **pandas** libraries for data analysis.<br>
Importing **matplotlib, seaborn libraries** for data visualisation and numerical extensions.<br>
Importing **sklearn** for different models and a different package for xgboost.<br>

# Exploratory Data Analysis (EDA)
We import dataset with a dataframe - 284807 rows and 31 columns<br>
- **_Null Values_**: There were no null values 
- **_Class Distribution_**: Distributing fraud and legitimate transaction numbers
            _ 0: Real - 284315  (99.827251%)_ <br>
             _1: Fraud - 492    (0.172749%) _<br>
- **_Checking correlation_ **with each 
             positive - positively corelated 
             negative - negatively corelated
- We use function of pandas : _TimeDelta_
             It represent a duration i.e. difference between two times 
             Therefore, we add three columns 
                       1. **df ['Time_day']**
                       2. **df ['Time_hour']**
                       3. **df ['Time_min']**
              Then, we drop the original Time column because its derivations are already considered.
              We observe that, column df['Time_day'] and ['Time_min'] do not have sufficient values.
              Therefore, we drop the above two columns and only consider the column ['Time_hour']
       
# Splitting data into train & test set
y - class (target variable)
x - everything except class
We split the dataset into two sets
- Test set size - 20%
- Train set size - 80%
Thus, the total values in the trainig and testing set are:
- **_Total set values - 492_**
- **_Train set values - 396_**
- **_Test set valuese - 96_**

# Visualising the distribution of variables
We have used a **_Histrogram_** for visualisation using functions like:
- **_enumerate function_** - to go through each column
- **_displot function_** - to plot histogram for each column of the datset
The **_green_** colour representing the normal transactions and
the **_red_** colour representing the fraud transactions.

# Model Building
We begin by creating a dataframe to store Results: 
             **_(df_Results)_**
             columns - Methodology, Model, Accuracy, roc_value, threshold

We create a **_common function_** for **_confusion matrix_**.
The common function is required to make a common method and procedure which can be called out everytime a model is established.

The models used are
1. **_Logistic Regression_**
2. **_K-Nearest Neighbours_**
3. **_Decision tree classifier_**
4. **_XG Boost_**
5. **_Support Vector Machine_**
             
We perform a **_cross validation_** with two methods
1. Repeated K-fold
2. Stratified K-fold

We create a dataframe with **_coefficient values_** for 
- checking most important coefficient values
- how each coefficient of feature contributes to the model

# Model Building with Balancing Classes
Since, our dataset is imbalanced, thus it may result in our model being imbalanced as it may give prefernce to the majority.
Therefore, we do Oversampling.
We use the following methods for Oversampling:
1. **_Random Oversample_**
2. **_SMOTE_**
3. **_ADASYN_**
      
# Hyperparameter Tuning
The hyperparameters taken into factor are:
1. max_depth
2. min_child_weight
3. n-estimators
4. learning_rate
5. gamma
6. subsample
7. colsample_bytree
 We use **_RandomizedSearchCV_** to check which parameter is the best and print the most important features of the best model to understand the dataset:
 Therefore,  **Top variable = 14**
             2nd Top variable = 17
             3rd Top variable = 18
 **The best model is XGBoost**
 We then calculate the roc value of XGBoost which is as follows: 
- ROC value - 0.9815403079438694
- Threshold value - 0.01721232570707798
             
 # Conclusion
 Therefore, in oversampling cases, **_XG Boost with Random Sampling with StratifiedKFold cross validation_** gives the best accuracy and ROC on oversampled data
 and **_Logistic Regression with L2 Regularisation for StratifiedKFold cross validation_** gives the best result for unsampled data.


 
 
  






           
             
