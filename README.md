# stroke_prediction
This project aims at predicting stroke with contributing health factors.
Data Source: 
The predictive models for stroke prediction is created on the dataset published in Kaggle (https://www.kaggle.com/fedesoriano/stroke-prediction-dataset).

Data Description:
The dataset contains 12 variables with 5110 rows. Below table shows all variables, their descriptions, and their type as they were loaded into R.

Variable Name	Variable Description	Variable Type
ID	Unique id	int
gender	Gender of patient	chr
age	Age of patient	num
hypertension	Hypertension (binary)	int
heart_disease	Heart disease (binary)	int
ever_married	Has the patient ever been married?	chr
work_type	Type of work	chr
Residence_type	Type of residence	chr
avg_glucose_level	Average glucose level in blood	num
bmi	Body Mass Index	chr
smoking_status	Has patient smoked	chr
stroke	Stroke (predictor variable)	int

Data Preprocessing
1. Missing Values: Missing values are present in columns BMI and gender. BMI variable is also of type chr when it should be numeric. First, we converted the column to numeric. Then, to deal with the missing values, we decided to impute them with the mean of the column. There is missing value in gender column. We decided to impute them with the mode, which was “female”. As a result, we did not exclude any rows from our dataset since all missing values are imputed.
2. Variable types: We converted gender, hypertension, heart_disease, ever_married, work_type, Residence_type and stroke columns to factors. 
3. Normalization: We normalized the continuous variables age, avg_glucose level and bmi.
4. Remove columns: removed the first ID column since we do not need to use it in our modeling.
5. Some of the variables have incorrect variable type. Hyper_tension, heart_disease and stroke variables are imported as “int” when they should be binary.

![image](https://user-images.githubusercontent.com/22393419/147868662-38c579a0-5b64-4d9b-8e87-5017edf1f968.png)
Fig 1: The number of people who had stroke in the dataset

![image](https://user-images.githubusercontent.com/22393419/147868680-daffa1b7-e8f5-44f0-9bbc-e487e8347e6d.png)
Fig 2: Gender of the people who suffered from stroke

![image](https://user-images.githubusercontent.com/22393419/147868689-e1325e05-6128-4e10-b9ef-e7ac389f4547.png)
Fig 3: Age distribution of the people who suffered from stroke

![image](https://user-images.githubusercontent.com/22393419/147868700-f3b95308-1c84-4b7e-a7ff-0ea281b18a66.png)
Fig 4: People who have/have not suffered from a stroke who have/don’t have hypertension

![image](https://user-images.githubusercontent.com/22393419/147868705-e351ab61-6adb-4920-a1fb-019f77d235e9.png)
Fig 5: BMI of the people who suffered from stroke

![image](https://user-images.githubusercontent.com/22393419/147868718-e020d35a-4c84-42ce-b100-7b75244dbf46.png)
Fig 6: People who have/have not suffered stroke and their smoking status

# Methdology:
Methodology 1: Logistic regression
We first used logistic regression as a starting point for classification task. It can fit more complex relationships than linear regression and is suitable for binary classification. We use glm function to do the regression. 
Methodology 2: Decision tree 
The second approach we did is the decision trees, and we used the c5.0 model in the decision trees. We thought this model will help us with the importance of each predictor variable and its impact on the target variable. 
We used the library c5.0 to do this. 
Methodology 3: Neural Network 
The third approach we tried was a neural network. We thought the approach was suitable for predicting stroke because of the architecture’s ability to generalize and understand complex relationships in the dataset, that a tree structure or rule-based algorithm might not detect.  We leveraged the ‘nnet’ package in R to fit a single layer neural network. The ‘nnet’ package also handles categorical inputs well as opposed to the R package ‘neuralnet’. 

Results:
All three models do a good job of predicting stroke with accuracy results ranging from 76% to 91%! When deciding on which model we would choose in a real-world application, we put ourselves in the shoes of a patient visiting a doctor for a wellness checkup. While the neural network model has the highest accuracy on test data, it lacks explain-ability which is critical in a medical application. If we take a different perspective, such as reporting for a news broadcast warning of risk of stroke, we might choose to report the neural network model and listing all the potential factors that weigh in on stroke risk.

Software used: R
