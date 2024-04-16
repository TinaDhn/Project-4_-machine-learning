# Project_4_Group_9
Project 4

## Diabetes Prediction Analysis

### Introduction

This repository contains code and analysis for predicting diabetes based on various factors using Python and machine learning techniques.

### Dataset

The dataset used for this analysis is named "Diabetes_Prediction_2018_2022.csv". It contains information about individuals' health-related attributes such as diabetes status, blood pressure, cholesterol levels, BMI, lifestyle factors, and demographic information.


#### Data Exploration

The analysis begins with exploring the dataset using pandas. Key steps include:
- Loading the dataset into a pandas DataFrame.
- Checking the first few rows, summary statistics, and data types of the variables.
- Examining the shape of the dataset to understand its dimensions.

The data contains no nulls. Many of the attributes are discrete in value, and most of these are binary. 

#### Variable Analysis

The analysis delves into understanding the relationship between various variables and diabetes status. Key steps include:
- Scaling the features using MinMaxScaler to ensure each feature contributes equally to the analysis.
- Visualizing the relationship between each feature and diabetes status using scatter plots.
- Creating a pairplot to visualize the pairwise relationships between different features.
- Calculating the correlation matrix to identify correlations between features and diabetes status.

Scaling had no effect on the pairplots, and scaling had no effect on the correlation heatmapping. Some variables that were more corrlated to each other when compared to other pairings were （PhysHlth, DiffWalk), (GenHlth, DiffWalk), (GenHlth, PhysHlth), (MentHlth, PhysHlth), and (GenHlth, MentHlth).
Diabetes_012 itself seemed to be the most highly correlated to GenHlth, HighBP, BMI, and DiffWalk compared to other attributes. 

#### Principal Component Analysis (PCA)

PCA is applied to reduce the dimensionality of the dataset and identify the key components contributing to diabetes prediction. Key steps include:
- Performing PCA on the dataset to extract principal components.
- Exploring the explained variance ratio to understand the contribution of each component.
- Visualizing the principal components using scatter plots and identifying the top contributing variables for each component.
- Analyzing the scatter plots for different combinations of principal components to understand their relationship with diabetes status.

This was done first without data scaling, and then again with scaling. Scaling **did** have an effect on PCA. Upon using scaling, the variability explained went from the top 3 principal components explaining 93% of the variability to then then needing the top 10 principal components to explain only 84% of the variability. 

Finding the top contributing attributes to each principal component revealed:
- **Before scaling**: mental health (MentHlth) was among the highest contributers for the top 4 principal components. For PC1, the top contributor was PhysHlth. For PC2, the top contributor was BMI. For PC3, the top was MentHlth. And, for PC4, the top contributor was Age.
- **After scaling**: Smoke was among the top contributors for PC1, PC2, and PC4. For PC1, the top contributor was HighBP. For PC2, the top contributor was Sex followed by Fruits. For PC3, the top contributor was Sex followed by PhysicalActivity. And, for PC1, the top contributor was Smoke followed by Fruits.

**Effect of scaling**: while scaling did create a PCA model whose variability isn't thoroughly explained by the first 3-5 principal components, scaling did provide principal components with more unique combinations of attributes that contributed to each component.

#### Logistic Regression Model

Logistic regression model is first used to analyze the non-diabetes and type-2 diabetes. This model is created in two different respectives: pre-processing dataset and processed dataset. The only difference between the two is processed dataset trims the number of data in non-diabetes to equal amount of data in type-2 diabetes. 

- **Logistic Regression Result (pre-processing dataset)** The model yields 86% accuracy score, but the result is hardly pursuasive because the precision and recall for type-2 diabetes is much lower than for non-diabetes. The cause of this issue is that number of data for this model between non-diabetes and type-2 diabetes are significantly inbalanced. Therefore we need to use processed dataset.

- **Logistic Regression Result (processed dataset)** The evaluation indicates that the model performs reasonably well in distinguishing between individuals with and without diabetes, with fairly balanced precision and recall for both classes. The overall accuracy of the model is 0.75, meaning 75% of instances whether an individual has diabetes or not were correctly predicted.

#### Decision Trees and Random Forest
Decision Tree consists of root node, decision node, and leaf node. Root node is the input or dataset that initiate the analysis; decision node contains a bunch of algorithm to process your data and determine the probability of model deicison; and leaf node is the output after combination processes from decision nodes.

Random Forest consists of multiple decision trees and generate a output based on the poll of decision trees. 

Considering our size of dataset, we knew that random forest will be the better option, but we do decision tree to make sure our hypothesis is correct.

- **Decision Tree Result** Decision Tree yields 66.8% on accuracy, 66% precision on non-diabete, 67% precision on type-2 diabetes, which is relatively lower compared to logistic regression.

- **Random Forest Result** Random forest yields 74.7% on accuracy, 77% precision on non-diabete, 73% precision on type-2 diabete, which is very similar to logistic regression model. Therefore I concluded that we can either use logistic regression or random forest to predict our result.

#### conclusion:

**From the Geomap:**
The more progressive states have a lower percentage diabetes compare to conservative 
-overall, trend for most age groups is positive with the exception of the younger age groups(18-44).
-trend is the people who have less than a high school degree have seen the most increased in diabetes.


**From relationships between variables:**
-Using pairplots on the variables in relation to diabetes, didn't exhibit clear relationships. 
Using a correlation heatmap highlighted a few more-highly correlated.
-Features that were most correlated with Diabetes included GenHlth, HighBP, BMI, and DiffWalk compared to other attributes. Scaling did not influence pairplots or correlation, as expected.

**From Statistical result:**
-Optimization plays a crucial role in machine learning. We were able to retrieve more robust results by utilizing techniques such as 
    1) Balancing Class Distributions (e.g., reducing the number of instances in the majority class) 
    2) Standard Scaling 
    3) Categorical Encoding (e.g., converting diabetes types into binary values).
-The overall accuracy of the model is 0.75, with precision of 0.76 for class 0 and 0.74 for class 1. Recall for class 0 is 0.74, and 0.77 for class 1. F1-score for class 0 is 0.75, and for class 1, it's 0.76.
-The evaluation indicates that the model performs reasonably well in distinguishing between individuals with and without diabetes, with fairly balanced precision and recall for both classes. However, it's essential to note that without additional context, it's challenging to fully assess the model's performance.


**From Supervised Learning:**
random forest has very similar accuracy with logistic regression model, decision tree model has the lowest accuracy among this 3 models. based on importance of features, BMI, High blod pressure, and High cholestrol have the most influences to the random forest model.


**From the neural network:**
3 different type of results,we get about 86% accuracy for analysing the non diabetes , type 1 diabetes and type 2 diabetes.
considering the accuracy the model at the network model is working, however, we still need to predict the actual results in the future.


**compare supervised learning vs neural network:**
supervised learning is more difficult to analyse model with more than 2 results. in this project neural network has easier assessment on the model that more than two results.


**Overall**
we have Logistic Regression with 76% accuracy in predicting type-2 diabetes
Also, Random Forest with 75% accuracy in predicting type-2 diabetes.
BMI, High blood pressure and High cholesterol have the most influences in random forest model
and Neural network (Highest Accuracy) with 86% accuracy in predicting type-2 diabetes.