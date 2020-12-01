# Section 4
## Model Performance Evaluation

Current Course material available at:

https://github.com/ChandraLingam/AmazonSageMakerCourse

Specifically for model performance at: 

https://github.com/ChandraLingam/AmazonSageMakerCourse/tree/master/PerformanceEvaluation

For Regression, we use Plots, Residual Histograms and RMSE Metric

For Binary Classification, we use Plots, Confusion Matrix, and Metrics like Precision, Recall, Accuracy, F1 Score, AUC Score and so forth

For Multiclass Classification, we use Plots, Confusion Matrix, Different ways to average class level metrics into model level metrics

# Regression Model Performance 

regression_model_performance.ipynb

RMSE 
Root mean squared error, find the difference between the actual and predicted value, square the difference for each observatoin of the dataset. 

Mean squared error is the average of the error for the entire dataset. 

To get the root mean squared error take the square root of that Mean Squared Error. Its going to be a smaller number as a result 

MSE of 787.38 becomes RMSE 28.06 

Smaller RMSE means a more accurate model, RMSE of 0 would mean 100 Accuracy of the model but might also indicate overfitting of the training set

Residual Histograms were also discussed as a way to compare which models under estimated and which models over estimated. 



# Binary classification


0/1 

True/False

Positive/Negative


Positive class is the condition we are interested in detecting, Negative class is the normal condition


Student Admitted To a Class
Positive = Admitted to class
Negative = Not admitted 

Heart Condition
Positive = Has heart condition
Negative = Normal patient

Is Email Spam 
Positive = Email is spam
Negative = Normal email


There are some algorithms that give a binary output and some algorithm give a probability of belonging to a positive class. If the result is above a threshhold then 

0/1 

or

 0.0 - 0.4 Negative
 0.5 - 1.0 Positive 


 Plots, Confusion Matrix, and Metrics like Precision, Recall, Accuracy, F1 Score, AUC Score

Plots are a good human readable way to guage the effectiveness but for tuning model performance a metric works better. 

 RAW Score or performance is better for tuning a model or automatically tuning parameters



### Confusion Matrix
Confusion Matrix is a table that summarizes performance of classification model.

_____
from sklearn.metrics import classification_report, confusion_matrix

or for help calculating it 
https://onlineconfusionmatrix.com/


It summarizes predictions into four categories:
True Positive = tp = how many samples were correctly classified as positive (count)
True Negative = tn = how many samples were correctly classified as negative (count)
False Positive = fp = how many negative samples were mis-classified as positive (count)
False Negative = fn = how many positive samples were mis-classified as negative (count)

Using these four metrics, we can derive other useful metrics like Recall, Precision, Accuracy, F1-Score and so forth.





# ROC Curve 
AUC - Area under curve is formed by plotting True Positive Rate against the false positive rate at different cutoff threshholds 

-----
from sklearn.metrics import roc_auc_score



Good models have AUC closer to 1

0.5 is considered random guess 

auc close to 0 indicates model is picking wrong results - flipping negative adn positive



# Multiclass classifier prediction

Similar to evaluating the performance of a binary classification, with a multi-class classification problem instead of a positive versus negative its a positive versus any other result is a negative for each of the classes 

- positive negative negative negative, then 
- negative positive negative negative, then 
- negative negative positive negative, then 
- negative negative negative positive, then done 

examples in multiclass classifier performance notebook

# F-1 
- the harmonic mean of precision and recall


Best description I have heard yet on the way to describe this. 



Regarding the Micro vs Macro average. 

-----
SciKitLearn classification report
micro vs macro average - good for determining a weight when imbalanced dataset are encountered. It provides a weighted average that takes imbalance in the distribution of classes in the dataset. 


macro average is not a good indicator when there are skewed class distributions. If 99% iof the data is not fraud, .5% is not, and .5% us unknown - macro would still treat all classes as equal 


## Quiz 

#### Question 1:
The Test RMSE scores for various models for predicting home prices are given below.  The median home price is USD 200,000.  Which model would you use?

Models with smaller RMSE value indicates better predictive quality.



#### Question 2:
In an email classifier, spam is considered positive, and normal email is negative. Model performance with test set is: TP=10, FN=5, TN=100, FP=20

How many spams are there in the test data set?
- 15 

Positive samples = TP + FN. You can find the spams in the test set by summing true positive and false negative. True positives are spams that were correctly classified. False-negative are spams that were misclassified as normal email.



#### Question 3:
In an email classifier, spam is considered positive, and normal email is negative.  Model performance with test set is: TP=10, FN=5, TN=100, FP=20

What is the recall for this model?
- 0.667 or .7 in the question


[For formula, refer to the Model Performance Evaluation.pdf in the downloadable resources of this section]

Recall or sensitivity
Recall = TP/(TP+FN). The recall is the probability of detecting spam. It does not consider misclassification of normal email as spam.



#### Question 4:
In an email classifier, spam is considered positive, and normal email is negative.  Model performance with test set is: TP=10, FN=5, TN=100, FP=20

What is the precision for this model?
- 0.3333 or .3 in the question 

[For formula, refer to the Model Performance Evaluation.pdf in the downloadable resources of this section]

Precision = TP/(TP+FP). With Precision, you can measure how many of the model predicted spams are really spams. Precision considers normal emails misclassified as spam.


#### Question 5:
In an email classifier, spam is considered positive, and normal email is negative.  Model performance with test set is TP=15, FN=0, TN=0, FP=120

What is the Recall for this model?
- 1.0 

[For formula, refer to the Model Performance Evaluation.pdf in the downloadable resources of this section]

In this example, the model is classifying all emails as spam. So, this model classified spam correctly but also misclassified all normal emails as spam. Recall = TP/(TP+FN). The recall does not consider misclassification of normal email as spam. If the recall is high, you should also look at precision and F1-score.



#### Question 6:
In an email classifier, spam is considered positive, and normal email is negative.  Model performance with test set is TP=15, FN=0, TN=0, FP=120

What is the F1-score for this model?
- 0.2 

In this example, the model is classifying all emails as spam. So, this model classified spam correctly but misclassified all normal emails as spam. It is a good idea to check both Recall and Precision Or use the F1-score. F1 Score = 2 * recall * precision/(recall + precision)



#### Question 7:
In an email classifier, spam is considered positive, and normal email is negative.  Model performance with test set is TP=1, FN=14, TN=120, FP=0

What is the Precision for this model?
- 1.0 

[For formula, refer to the Model Performance Evaluation.pdf in the downloadable resources of this section]

In this example, the model is classifying almost all emails as normal. It detected only one spam correctly, and all other emails were classified as normal. Precision is high because it did not misclassify any normal email as spam. Precision = TP/(TP+FP). When precision is very high, you should also look at the recall or F1-score.

#### Question 8:
In an email classifier, spam is considered positive, and normal email is negative.  Model performance with test set is TP=1, FN=14, TN=120, FP=0

What is the F1-score for this model?
- .125 or 0.1 as the closer option given 

[For formula, refer to the Model Performance Evaluation.pdf in the downloadable resources of this section]



