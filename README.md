# Amazon-Anomaly-Detection
This Capstone project was done as a part of my data science course.
## Business Problem
- The e-commerce sales are surging which has increased the significance of online reviews and product ratings in influencing the decisions made by the users in day-to-day life. The users make use of these ratings and reviews to help them to make their respective purchases. However, there have been instances where these product ratings and reviews given by a customer do not synchronize with each other, which leads to the downfall of the reliability of the customer ratings. This gives birth to anomalies present between the ratings and reviews given by a customer.

- In this project, the focus is on the domain of reviews and ratings received on an e-commerce website, precisely for Amazon.com. The goal is to identify any inconsistencies between the ratings and the reviews given by a customer, thereby confirming if the rating is in line with the review. The importance of checking for such irregularities is significant and critical as could lead to actionable information and helps to gauge the customer response concerning product reviews and ratings.

## Project Overview
- The objective is to identify any inconsistencies or anomalies between the ratings and the reviews given by a customer, thereby confirming if the rating is in line with the review.
- Performed EDA to understand the relation of target variable with the other features.
- Statistical Analysis techniques like one-sample z-test was performed to get an optimal threshold value for prooving the Null Hypothesis stating that weighted recall is 95%. For this analysis, the significance level is 0.05. Specifically, the approach is appropriate because the sampling method was simple random sampling, the sample included at least 10 successes and 10 failures, and the population size was at least 10 times the sample size.
- Different models such as Logistic Regression, Decision Tree, Random Forest, AdaBoost,Gradient Boost, XGB Boost and Multinomial Naive Bayes were build using K-Fold Cross Validation.
- XGB Boost gave the best results in terms of bias- variance trade off, and thus the hyper parameters were tuned for the same in order to get the optimal results.
- It is established that manual labeling is required to evaluate the model, to see how good the model is in predicting and not predicting the anomaly.Therefore, a sample is taken from 40.8k records to evaluate the model and manual labeling is also performed for this sample.
- Because of severe class imbalance,the default threshold can result in poor performance. As such, a simple and straightforward approach to improve the performance of a classifier that predicts probabilities on an imbalanced classification problem is to tune the threshold used to map probabilities to class labels.



