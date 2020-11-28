Working with:
AmazonSageMakerCourse 
- introduction
- ml_handling_missing_values.ipynb

df.isna().any(axis=0)
lets see where the missing values are

Good review of missing values and when it is a good idea to use the different ways to deal with missing values. Good visualization on how it affects the values in the dataframe 
- df.dropna()
    - Remove row with missing values
- df.mean()
    - mean of the entire dataset
- df.['Vehicles'].interpolate()
    - connects straight line from last known datapoints adjacent to the missing values 
- df.['Vehicles'].fillna(method='ffill')
    - Replace missing values with previous valid value for that attribute
- df.['Vehicles'].fillna(method='bfill')
    - Replace missing values with next valid value for that attribute

Interpolation is a good choice for timeseries data, such as the traffic on a road at given hours of a day. 

If the dataset contained information about the traffic on different roads that are independent of one another interpolation may not make sense. 

#### Iris dataset 
sepal_length/width
petal_length/width

For this dataset if there were missing values it may not make sense to imput the missing data as the mean of the entire dataset. 


Three classes of flowers to identify
- Iris-setosa
- Iris-versicoloe
- Iris-virginica


The reason is because each of the species of iris have distinct difference in the width/length of petals and sepal

```
group_class = df.groupby('class')
```

```
group_class.mean()
```
This shows us the mean is different for each of the groups that need to be classified. If there were missing values in individual classes it would make more sense to replace missing values with the mean of individual classes rather than the mean of the entire dataset. 


For example the groupclass mean of the entire dataset for petal_width is 1.205 but for individual classes:
- setosa            0.246
- versicolor        1.326
- virginica         2.026



now back to the groupby class idea, we can see it put into action by applying the mean of missing values based on the mean of the class we are predicting rather than the entire data set. 

For each group, use group level averages to fill missing values
```
df['sepal_length'] = group_class['sepal_length'].transform(lambda x: x.fillna(x.mean()))
df['sepal_width'] = group_class['sepal_width'].transform(lambda x: x.fillna(x.mean()))
df['petal_length'] = group_class['petal_length'].transform(lambda x: x.fillna(x.mean()))
df['petal_width'] = group_class['petal_width'].transform(lambda x: x.fillna(x.mean()))
```

There we used the group_class to do a transform lambda apply 







---
### Data Visualization - Linear, Log, Quadratic and More


