# Himalayan Expedition Data Analysis

## Overview of the Project

### Selected Topic

Sponsorship of Himalayan Climbing Expeditions

### Reason for Choosing Topic

The South Palm (an outdoor apparel and equipment company) hired our analytics consulting group to assist in assessing the success probability of a given sponsorship candidate. Our team was able to acquire data sets for individuals, expedition team, and peaks, all within the Himalayan Range.
Using this data, our team is performing exploratory and  predictive analysis to assess success. Features used to complete this analysis include the climber’s gender and age as well the chosen peak, season of scheduled climb,  use of oxygen, and team size the climber intends to be on.


### Data Sources 

* expeditions.csv

* members.csv

* peaks.csv


From:  https://www.kaggle.com/majunbajun/himalayan-climbing-expeditions

#### Data Description:

The data is a compilation of records for all expeditions that have climbed in the Nepal Himalaya. 
It is based on the expedition archives of Elizabeth Hawley, a longtime journalist based in Kathmandu, and it is supplemented 
by information gathered from books, alpine journals and correspondence with Himalayan climbers.

##### Expeditions
Data for each expedition team attempting climbs in the Himalayan Range.

##### Members
Data for each individual on each expedition attempting climbs in Himalayan Range.

##### Peaks
Data for peaks within the Himalayan Range.

### Questions to be answered

Given a person’s age, sex, season of expedition undertaken, the number of members in the team, and peak height, we hope to predict whether the person will succeed in his/her sponsored expedition.

For the purposes of these questions, success is defined by an individual summiting the attempted peak and surviving the climb.



### Link to Google Slide Deck

https://docs.google.com/presentation/d/1bRTnpVQG-WUjvTTX9XkN1d-kavw5SEjPLEnOTBMfNOc/edit#slide=id.g10d202b0a28_0_15

### Link to Tableau Workbook

https://public.tableau.com/app/profile/muru4340/viz/HimExpDataExp_16437668499040/HimalayanDataAnalysis?publish=yes

## Overview of the Analysis

### A. Descriptive Analysis

Analyze trends between different variables in the dataset including: age, sex, team size, # of hired staff, peak, peak height, and season to success rates. Use visualizations in tableau to get a rough idea of which variables are correlated with success and which ones have minimal to no effect on success. The following graphs/visualizations were created to aid in the process:

  1. Age vs Success
  2. Peak Height vs Success
  3. Success by Team size 
  4. Success by Hired Staff
  5. Count of climbs vs season
  6. Season vs success
  7. Sex vs success

Also, each of these varialbes were filtered by peak, age, and peak height to see what changes based on what peak someone climbs and how old the climber is. 


### B. Predictive Analysis
#### 1. Data Pre-processing

The data was preprocessed for the machine learning algorithm in following steps:

1. The raw data file was cleaned for all the null values, duplicate rows, and the outliers.
2. It was then stored in AWS postgres database from it was read into the machine learning code.
3. Before treating it with the algorithm, some of the features that are redundant and not useful was dropped.
4. The target variable was checked for any class imbalance that could potentially affect the performance of the algorithm.
5. The data was further processed for feature selection and engineering as discussed below.

#### 2. Date Exploration for Feature Selection and Engineering

The feature engineering for the machine learning algorithm was carried out in following steps:

1. The categorical columns in the dataset were encoded using the one-hot-encoding technique.
2. This resulted in additional columns
3. The columns were scaled using the StandardScaler and transformed to make sure that each feature had zero mean and a variance of 1.

The feature selection was carried out in following steps:

1. The data was explored to look for correlation between the dependent variable (target) and the independent variables (features)
2. The data was then explored to look for any strong correlation between the independent variables (features)
3. A correlation matrix was generated for the above purpose.
4. A function was written to scan through all the correlations in the matrix and determine pairs that had correlation coefficient of 0.7 or more.
5. Among the pair that had correlation coefficient 0.7 or more, one of the feature was kept and the other was dropped.
6. This resulted in a set of features that had correlation coefficient of less than 0.7 between each other.
7. The final selected features were than used in machine learning algorithm.

#### 3. Choosing Machine Learning Models

The machine learning model for the dataset was built using the following algorithms:

1. Logistic Regression (LR)
2. K Nearest Neighbor (KNN)
3. Decision Tree (DT)
4. Neural Network (Multilayer Perceptron - feed forward neutral network)(NN)
5. Balanced Random Forrest (BRF)
6. Easy Emsemble AdaBoost (EEA)

The choice of these algorithms were based on the type of data that we are modelling. The himalayan data is a labelled data with both input and the output given. The most appropriate approach for this kind of dataset is the supervised machine learning models. Since the data has only two class (Success and Failure), it belongs to a classification type and the above algorithms are the most suitable ones. We decided to use several supevised learning algorithms in the hope to understand and improve the model performance. Some model resulted in a modest accuracy, whereas other showed significant improvement. The limitation of some models and the benefit of others was obvious.

#### 4. Model Performance Evaluation

The performance of the model was evaluated using the following metrics:

1. Confusion matrix and accuracy score
2. Receiver operating characteristics (ROC) curve and the AUC score.

## Results
The descriptive analysis of the data led us to determine which variables were most correlated with success and which weren't. The varialbes that most affected success rates were:

  1. Age
  2. Peak Height
  3. Team Size
  4. Hired Staff

The variables that were not correlated or showed minimal effect were:

  1. Season
  2. Sex

The predictive analysis of the himalayan expedition data indicate that the Random Forrest machine learning algorithm comes close to 84% in predicting whether an applicant will succeed in his/her expedition. While this may not be enough for our client, South Palm, and an accuracy of over 90% would be more desirable, the current analysis can be improved by:

1. Choosing a different feature selection technique, such as, the wrapper method, or the embedded method.
2. By using feature extraction technique, such as the Principal Component Analysis (PCA).
