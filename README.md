# Cardiovascular Disease Project
### By Jeremy Jung and Andrew Osorio

In this project, we used a cardiovascular disease dataset to train classification models to predict if a patient would have cardiovascular disease, based on the various risk factors and features they had. We sourced the data from https://www.kaggle.com/sulianova/cardiovascular-disease-dataset. The data contained 70,000 records of patient data and included 11 features about each patient, such as age, height, and glucose levels, as well as the target variable, a binary value indicating if cardiovascular disease was present in the patient.

#### Data processing
We started with feature engineering and data manipulation. We created a few new features in the dataset, including BMI, which gives a useful measurement on body fat when considering height and weight, as well as a discrete feature, blood pressure, which gives a score of 0-4 based on how high someone's blood pressure is. We also found that there were errors in the dataset for both systolic and diastolic blood pressure readings for a few select patients, so we created floors and ceilings for max readings for both of these values at the 5th and 95th percentile, or two standard deviations away from the mean.

#### Visualizations
We created a couple of visualizations of the data to better understand what features impact the presence of cardiovascular disease. We found, for example, that people with higher levels of cholesterol were proportionately more at risk for cardiovascular disease, and people with higher weights at the same height appeared to be more at risk as well.

![Cholesterol](https://github.com/triple-jay/cardio/blob/master/Images/cholesterol.png)

#### Training models
We split the data into a train and test set, and we used various classification algorithms to train different models on the train data.

We used the following classification models and achieved the following accuracy scores on the test data:
* Decision Tree Classifier: 0.733429
* Logistic Regression: 0.725214
* KNN: 0.684000
* Perceptron: 0.566143
* Random Forest: 0.735786

On our best model, the __random forest__, we performed cross validation and found a similar accuracy of __73.3%__.

#### Further optimization and results
The random forest comes with a very useful feature, which shows us the importance of the different features of the dataset on determining the model itself. We dropped the features of lowest importance, which we found were not important to the random forest and would most likely create unhelpful noise in the dataset and create unnecessary variance. We found that the gender of the patient, as well as the binary variables determining if the patient smoked or drank alcohol, were not adding much information to the classifier. We dropped these features. Running a cross validation on the random forest again, we found this raised our accuracy to __73.4%__, a minor improvement.

![Feature-importance](https://github.com/triple-jay/cardio/blob/master/Images/featureimportance.png)

Using our three best models, the decision tree, random forest, and logistic regression, we ran a voting classifier to see if this would improve our overal score. We achieved an accuracy of __73.5%__ on cross validation, which turned out to be our best score.

Through our data visualizations, we found that the most important factors for cardiovascular disease were cholesterol, blood pressure levels, and age. These results were fairly consistent with our hypothesis. 

#### Future improvements
In the future, we hope to continue to improve on this experiment by finding new ways to engineer new features. We believe we could have improved our score further had we found a more clever way to engineer features. We also hope to improve by learning new machine learning models. Although we chose a small subset of classification models for our analysis, we realize that there are so many other algorithms that we can apply to this model, and we hope through further research we could potentially find one that works even better than the ones we have now.
