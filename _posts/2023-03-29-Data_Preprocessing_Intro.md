---
title: Data Preprocessing Introduction
author: SeHoon
date: 2023-03-29 15:30:00 +0900
categories: [Machine Learning, ML_Introduction]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is data preprocessing?<br>

Data preprocessing is an important task that must be conducted before a dataset can be used for model training. Raw data is often noisy and unreliable, and may be missing values. Using such data for modeling can produce misleading results.<br>
To solve the misleading, five main tasks are performed in data preprocessing:<br>
+ **Data cleaning**: Fill in missing values, detect, and remove noisy data and outliers.<br>
+ **Data transformation**: Normalize data to reduce dimensions and noise.<br>
+ **Data reduction**: Sample data records or attributes for easier data handling.<br>
+ **Data discretization**: Convert continuous attributes to categorical attributes for ease of use with certain machine learning methods.<br>
+ **Text cleaning**: Remove embedded characters that may cause data misalignment, for example, embedded tabs in a tab-separated data file, or embedded new lines that may break records.<br>

# What is the order of data preprocessing?<br>
1. **Taking care of missing data**<br>
2. **Encoding categorical data**<br>
3. **Splitting the dataset into the training set and test set**<br>
4. **Feature scaling**<br><br>

There are more details in the [Data preprocessing](https://csh970605.github.io/posts/Data_Preprocessing/) post.<br>
<br>


