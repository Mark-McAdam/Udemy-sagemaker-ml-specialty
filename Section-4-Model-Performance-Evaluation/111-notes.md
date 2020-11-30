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



