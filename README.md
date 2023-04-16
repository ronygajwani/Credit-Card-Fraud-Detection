# Credit-Card-Fraud-Detection
Analysis of different machine learning algorithms for credit card fraud detection

IMPORTING DEPENDENCIES
Importing numpy and pandas libraries for data analysis.Importing matplotlib, seaborn libraries for data visualisation and numerical extensions.
Importing sklearn for different models and a different package for xgboost.

EXPLORATOTY DATA ANALYSIS (EDA)
We import dataset with a dataframe - 284807 rows and 31 columns
- Null Values: There were no null values 
- Class Distribution: Distributing fraud and legitimate transaction numbers
             0: Real - 284315  (99.827251%)
             1: Fraud - 492    (0.172749%)
- Checking correlation with each 
             positive - positively corelated
             negative - negatively corelated
- We use function of pandas : TimeDelta
             It represent a duration i.e. difference between two times 
             Therefore, we add three columns 
                       1. df ['Time_day']
                       2. df ['Time_hour']
                       3. df ['Time_min']
              Then, we drop the original Time column because its derivations are already considered.
              We observe that, column df['Time_day'] and ['Time_min'] do not have sufficient values.
              Therefore, we drop the above two columns and only consider the column ['Time_hour']
       
SPLITTING DATA INTO TRAIN AND TEST
y - class (target variable)
x - everything except class
We split the dataset into two sets
             Test set size - 20%
             Train set size - 80%
Thus, the total values in the trainig and testing set are:
             Total set values - 492
             Train set values - 396
             Test set valuese - 96

VISUALISING THE DISTRIBUTION OF VARIABLES
We have used a Histrogram for visualisation using functions like:
             enumerate function - to go through each column
             displot function - to plot histogram for each column of the datset
The green colour representing the normal transactions and
the red colour representing the fraud transactions.

MODEL BUILDING
We begin by creating a dataframe to store Results: 
             (df_Results)
             columns - Methodology, Model, Accuracy, roc_value, threshold

We create a common function for confusion matrix.
The common function is required to make a common method and procedure which can be called out everytime a model is established.

The models used are
             1. Logistic Regression
             2. K-Nearest Neighbours
             3. Decision tree classifier
             4. XG Boost
             5. Support Vector Machine
             
We perform a cross validation with two methods
             1. Repeated K-fold
             2. Stratified K-fold

We create a dataframe with coefficient values for 
             - checking most important coefficient values
             - how each coefficient of feature contributes to the model

MODEL BUILDING WITH BALANCING CLASSES
Since, our dataset is imbalanced, thus it may result in our model being imbalanced as it may give prefernce to the majority.
Therefore, we do Oversampling.
We use the following methods for Oversampling:
             1. Random Oversample
             2. SMOTE
             3. ADASYN
      
HYPERPARAMETER TUNING
The hyperparameters taken into factor are:
             1. max_depth
             2. min_child_weight
             3. n-estimators
             4. learning_rate
             5. gamma
             6. subsample
             7. colsample_bytree
 We use RandomizedSearchCV to check which parameter is the best and print the most important features of the best model to understand the dataset:
 Therefore,  Top variable = 14
             2nd Top variable = 17
             3rd Top variable = 18
 The best model is XGBoost.
 We then calculate the roc value of XGBoost which is as follows: 
             ROC value - 0.9815403079438694
             Threshold value - 0.01721232570707798
             
 CONCLUSION
 Therefore, in oversampling cases, XG Boost with Random Sampling with StratifiedKFold cross validation gives the best accuracy and ROC on oversampled data
 and Logistic Regression with L2 Regularisation for StratifiedKFold cross validation gives the best result for unsampled data.


 
 
  






           
             
