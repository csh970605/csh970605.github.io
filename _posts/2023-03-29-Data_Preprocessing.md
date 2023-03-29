---
title: Data Preprocessing Introduction
author: SeHoon
date: 2023-03-29 20:30:00 +0900
categories: [Vision Machine Learning, Theory]
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


## How to normalize data?
---
<br>

+ **Min-Max Normalization**: Linearly transform the data to a range, say between 0 and 1, where the min value is scaled to 0 and max value to 1.<br>
+ **Z-score Normalization**: Scale data based on mean and standard deviation: divide the difference between the data and the mean by the standard deviation.<br>
+ **Decimal scaling**: Scale the data by moving the decimal point of the attribute value.<br>
