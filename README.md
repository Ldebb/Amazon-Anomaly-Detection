# Amazon-Anomaly-Detection
This Capstone project was done as a part of my data science course.
## Business Problem
- The e-commerce sales are surging which has increased the significance of online reviews and product ratings in influencing the decisions made by the users in day-to-day life. The users make use of these ratings and reviews to help them to make their respective purchases. However, there have been instances where these product ratings and reviews given by a customer do not synchronize with each other, which leads to the downfall of the reliability of the customer ratings. This gives birth to anomalies present between the ratings and reviews given by a customer.

- In this project, the focus is on the domain of reviews and ratings received on an e-commerce website, precisely for Amazon.com. The goal is to identify any inconsistencies between the ratings and the reviews given by a customer, thereby confirming if the rating is in line with the review. The importance of checking for such irregularities is significant and critical as could lead to actionable information and helps to gauge the customer response concerning product reviews and ratings.

## Project Overview
- The objective is to identify any inconsistencies or anomalies between the ratings and the reviews given by a customer, thereby confirming if the rating is in line with the review.
- Since the data deals with textual data, therefore different NLP Techniques were used for pre-processing the data. 
- Performed EDA to understand the relation of target variable with the other features.
- Statistical Analysis techniques like one-sample z-test was performed to get an optimal threshold value for prooving the Null Hypothesis stating that weighted recall is 95%. For this analysis, the significance level is 0.05. Specifically, the approach is appropriate because the sampling method was simple random sampling, the sample included at least 10 successes and 10 failures, and the population size was at least 10 times the sample size.
- Different models such as Logistic Regression, Decision Tree, Random Forest, AdaBoost,Gradient Boost, XGB Boost and Multinomial Naive Bayes were build using K-Fold Cross Validation.
- XGB Boost gave the best results in terms of bias- variance trade off, and thus the hyper parameters were tuned for the same in order to get the optimal results.
- It is established that manual labeling is required to evaluate the model, to see how good the model is in predicting and not predicting the anomaly.Therefore, a sample is taken from 40.8k records to evaluate the model and manual labeling is also performed for this sample.
- Because of severe class imbalance,the default threshold can result in poor performance. As such, a simple and straightforward approach to improve the performance of a classifier that predicts probabilities on an imbalanced classification problem is to tune the threshold used to map probabilities to class labels.

## Dataset Description
- The online reviews for Amazon.com data has been procured from Kaggle having 67,992 records and ten attributes.
- In addition to this, have also used the combined 3000 reviews of IMDB, Yelp.com and Amazon.com that details reviews labelled with sentiment score. This dataset was created for the paper From Group to Individual Labels using Deep Features, Kotzias et. al,. KDD 2015.

## EDA & Suggested Solutions to the problem
- Removing 2,3,4 ratings from the dataset as it is impossible to rectify anomalies, visualising the dataset.
- Sentiment analysis method is performed using TextBlob text polarity to make training records sufficient for model evaluation. 
- The training dataset with 3K records requires text-cleaning before Model building.
- NLP Techniques such as: Lowercase Reviews, Punctuation Special Character removal (using Regex),Spelling Corrections(Using Textblob), Lemmatization, Removing Stop words
were performed.
- Since these records weren’t dynamic, therefore, 7k records (without anomalies) are added from the amazon dataset using the same pre-processing steps to help in better training of the model.
- Metrics scores of TF-IDF are better, therefore it is chosen over Count Vectorizer for Text to numeric conversion.

## Evaluation Metric
- Weighted Recall was chosen as the metric for anomaly detection.

## Model Performance
- In order to achieve the best results different linear and non-linear models on the basis of different scoring metrics namely: Accuracy, Roc_Auc, F1-Score  were build using K-Fold Cross Validation, where Number of Splits is considered as 7.
- For both Accuracy & F-1 Scoring metrics, XGB Classifier gives the best Bias Accuracy and Variance Error Trade Off.
- Using Grid Search CV hyper paramters were tuned for XGB Classifier where n_estimators : 200, max_depth: 15, Learning_rate:  0.1 was selected.
- As mentioned above because of manual labeling the anomalies( where rating were not aligned with the reviews), a sample size of 400 was taken out of 40k records with 5% margin of error, 95% Confidence Interval, 10% expected sample proportion(having anomaly) was taken.
- In actuality there were 16 anomalies(Y_true) in the 400 samples, however the model predicted 51 anomalies(Y_pred), which was calculated by comparing model pred ratings and the user(actual) ratings.

## Evaluation
- Model is able identify all the anomalies, but it wrongly identified few non-anomalies as anomalies, which further resulted in 35 False positives and 0 False Negatives.
- FN is costlier for this particular business case. 
- The above results are obtained with the default threshold of 0.5. In order to get more better results by decreasing the amount of False Positives without compromising on False Negatives, different thresholds were tuned.
- Since False Negatives are more costlier, thus aim was to maximize the recall.

## Statistical Data Analysis
- Hypothesis:
Null hypothesis: Weighted Recall = 0.95
Alternate Hypothesis: Weighted Recall ≠ 0.95

## Conclusion
- After tuning the threshold to different values using XGB Classifier, 0.4 threshold gave the best results, ith a pvalue >0.05. Which further means that the null hypothesis holds true.
- Obtained a 100% Recall, ie: False Negatives are 0 and a reduction in False Positives from 35 to 28 was observed.

## Business Recommendation:

FP only costs a message that is sent to the user whereas FN affects the users’ trust on the website as it directly affects the ratings. So to the client, recommendation can be to send a text message/email to the user to inform them about the difference between their rating and review thus allowing them to change their rating or review. Hence, the rating will be true to users’ experience. 






























