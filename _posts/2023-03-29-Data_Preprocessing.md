---
title: Data Preprocessing
author: SeHoon
date: 2023-03-29 20:30:00 +0900
categories: [Machine Learning, ML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---
# What is data preprocessing?<br>

Data preprocessing is a important task that must be conducted before a dataset can be used for model training.<br>
Raw data is often noisy and unreliable, and may be missing values. <br>
Using such data for modeling can produce misleading results.<br>

# The need of preprocessed and clean data<br>

Real world data is gathered from various sources and processes and it may contain irregularities or corrupt data compromising the quality of the dataset.<br>
The typical data quality issues that arise are

+ **Incomplete**: Data lacks attributes or containing missing values.<br>
+ **Noisy**: Data contains erroneous records or outliers.<br>
+ **Inconsistent**: Data contains conflicting records or discrepancies.<br><br>

Quality data is a prerequisite for quality predictive models.<br>
To avoid "garbage in, garbage out" and improve data quality and therefore model performance, it is imperative to conduct a data health screen to spot data issues early and decide on the corresponding data processing and cleaning steps.<br><br>

# The major tasks in data preprocessing

+ **Data cleaning**: Fill in missing values, detect, and remove noisy data and outliers.<br>
+ **Data transformation**: Normalize data to reduce dimensions and noise.<br>
+ **Data reduction**: Sample data records or attributes for easier data handling.<br>
+ **Data discretization**: Convert continuous attributes to categorical attributes for ease of use with certain machine learning methods.<br>
+ **Text cleaning**: remove embedded characters that may cause data misalignment. For example, embedded tabs in a tab-separated data file, embedded new lines that may break records, for example.

# What is the order of data preprocessing?<br>
1. **Taking care of missing data**<br>
2. **Encoding categorical data**<br>
3. **Splitting the dataset into the training set and test set**<br>
4. **Feature Scaling**<br><br>

## Why conduct splitting before feature scaling?<br>
---
<br>

Because the average and standard deviation of the training set affect the average and standard deviation of the test set when feature scaling is performed first.<br><br>

## How to take care of missing values?<br>
---
<br>

+ **Deletion**: Remove records with missing values<br>
There is an example of conducting Deletion<br>
You can see the example code below.<br>

```py
from sklearn.impute import SimpleImputer
import numpy as np

imputer = SimpleImputer()
imputer.fit(X[:, 1:3])
X[:, 1:3] = imputer.transform(X[:, 1:3])
```
<br>

+ **Dummy substitution**: Replace missing values with a dummy value: e.g, unknown for categorical or 0 for numerical values.<br>
There is an example of conducting Deletion<br>
You can see the example code below.<br>

```py
from sklearn.impute import SimpleImputer
import numpy as np

imputer = SimpleImputer(missing_values=np.nan, strategy='constant')
imputer.fit(X[:, 1:3])
X[:, 1:3] = imputer.transform(X[:, 1:3])
```
<br>

+ **Mean substitution**: If the missing data is numerical, replace the missing values with the mean.<br>
There is an example of conducting Deletion<br>
You can see the example code below.<br>

```py
from sklearn.impute import SimpleImputer
import numpy as np

imputer = SimpleImputer(missing_values=np.nan, strategy='mean')
imputer.fit(X[:, 1:3])
X[:, 1:3] = imputer.transform(X[:, 1:3])
```
<br>
<br>

+ **Frequent substitution**: If the missing data is categorical, replace the missing values with the most frequent item<br>
There is an example of conducting Deletion<br>
You can see the example code below.<br>

```py
from sklearn.impute import SimpleImputer
import numpy as np

imputer = SimpleImputer(missing_values=np.nan, strategy=most_frequent)
imputer.fit(X[:, 1:3])
X[:, 1:3] = imputer.transform(X[:, 1:3])
```
<br>
<br>

## Why and how to Encoding categorical data?
---
<br>
The reason for encoding is to create a string value as a binary vector that is easy for computers to recognize.<br>
The reason why it is not a simple "int value" is that it can recognize that there is a correlation between codes during machine learning.<br>
There are example codes and results below<br>

```py 
# Example code
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder
ct = ColumnTransformer(transformers=[('encoder', OneHotEncoder(), [0])], remainder='passthrough')
X = np.array(ct.fit_transform(X))
```

<br><br>
**result of raw values**

```
[['France' 44.0 72000.0]
 ['Spain' 27.0 48000.0]
 ['Germany' 30.0 54000.0]
 ['Spain' 38.0 61000.0]
 ['Germany' 40.0 63777.77777777778]
 ['France' 35.0 58000.0]
 ['Spain' 38.77777777777778 52000.0]
 ['France' 48.0 79000.0]
 ['Germany' 50.0 83000.0]
 ['France' 37.0 67000.0]]
```
<br>

**result of changes in values**

```
[[1.0 0.0 0.0 44.0 72000.0]
 [0.0 0.0 1.0 27.0 48000.0]
 [0.0 1.0 0.0 30.0 54000.0]
 [0.0 0.0 1.0 38.0 61000.0]
 [0.0 1.0 0.0 40.0 63777.77777777778]
 [1.0 0.0 0.0 35.0 58000.0]
 [0.0 0.0 1.0 38.77777777777778 52000.0]
 [1.0 0.0 0.0 48.0 79000.0]
 [0.0 1.0 0.0 50.0 83000.0]
 [1.0 0.0 0.0 37.0 67000.0]]
```


<br><br>

## How to split dataset into the training set and test set?
---
<br>

```py
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, 
                                                    y, 
                                                    test_size=0.2, 
                                                    random_state=1, 
                                                    shuffle=False)
```

<br><br>

## How to normalize data?
---
<br>

+ **Min-Max Normalization**: Linearly transform the data to a range, say between 0 and 1, where the min value is scaled to 0 and max value to 1.<br>
$scaled\ value = $ $(original\ value - mean\ of\ data)\over (max\ of\ data - min\ of\ data)$<br>
You can see the example code below.<br>

```py
from sklearn.preprocessing import MinMaxScaler
sc = MinMaxScaler()
X_train[:, 3:] = sc.fit_transform(X_train[:, 3:])
X_test[:, 3:] = sc.transform(X_test[:, 3:])
```
<br>

+ **Z-score Normalization**: Scale data based on mean and standard deviation: divide the difference between the data and the mean by the standard deviation.<br>
$scaled\ value = $ $(original\ value - mean\ of\ data)\over standard\ deviation\ of\ data$<br>
You can see the example code below.<br>

```py
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
X_train[:, 3:] = sc.fit_transform(X_train[:, 3:])
X_test[:, 3:] = sc.transform(X_test[:, 3:])
```
<br>
<br><br>
<br>

# Implementation

+ [Data Preprocessing Template](https://github.com/csh970605/Machine-LearningA-Z/tree/main/Part%201%20-%20DataProcessing/Section2/Python)
