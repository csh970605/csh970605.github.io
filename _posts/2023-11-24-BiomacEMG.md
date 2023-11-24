---
title: BiomacEMG
author: SeHoon
date: 2023-09-15 10:42:30 +0900
categories: [Papers, Bio]
tags: [Papers, Bio, AMRLabs]
math: true
mermaid: true
---

# What is BiomacEMG?

BiomacEMG is a concept that is suggested by [Article](https://www.mdpi.com/2076-3417/13/9/5744).
<br>
In the article, biomacEMG classifies 7 handgestures with Machine Learning. <br>
Then, let's see how it works.
<br><br><br><br>


# What is EMG?

EMG(electromyography) is a type of physiological signal recording that detects electrical signals from muscle fibres in response to gestures or movements.<br>

<br><br><br><br>

# What does BiomacEMG do?

The article uses surface electrodes to collect electromyographic (EMG) data from
the forearm flexion and extension muscles, which were used as input parameters to the
machine learning algorithms to recognize seven hand gestures.<br>

Since EMG signals are erratic, signal analysis performance is generally poor, they measure different types of muscle gropus in real time. Which is:

+ The carpi radials of the muscle flexor are responsible for the flexion and radial deviation of the wrist.<br>

+ Musculus flexor pollicis longus, which is responsible for the flexion of the pollicis.<br>

+ The carpi radials of the muscle flexor are responsible for the flexion and radial deviation of the wrist.<br>

+ Musculus flexor pollicis longus, which is responsible for the flexion of the pollicis.<br>

+ Musculus flexor digitorum, which is responsible for flexion of the fingers.<br>

+ The carpi ulnaris muscle flexor, which is responsible for flexion and ulnar deviation
of the wrist.<br>

+ Muscuclus extensor pollicis longus at brevis, which is responsible for the extension of
pollicis.<br>

+ The carpi ulnaris muscle extensor is responsible for extension and ulnar deviation of
the wrist.<br>
+ Musculus extensor digitorum, that is responsible for extension of the fingers.<br>

+ Musculus extensor carpi radialis, which is responsible for extension and radial deviation of the wrist.<br>

You can see which muscles are used at the pictures below:
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/39c46a76-ef03-45ee-8885-10b1a8f93e85" width="330" height="300"><img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/a54f1c86-ba1e-4ce2-ae9d-18bc0cc83bef" width="350" height="300">
</center>
<br><br>
<br><br>

# Steps of classifing gestures

1. Feature extraction<br>
    In this article, it extracted 9 features which are:

    + Standard deviation

    + Minimum

    + Maximum

    + Crossing the zero axis

    + Average change in amplitude

    + The first amplitude jump

    + Mean absolute value

    + Wave length

    + Wilson amplitude

    Each methods will be explaned below.

2. [PCA](https://csh970605.github.io/posts/PCA/)

3. [Random Forest Classification](https://csh970605.github.io/posts/Random_Forest_Classification/)

4. Pareto Optimization

<br><br>

## Standard Deviation
Standard deviation is a measure of absolute variability that shows how individual
observations are grouped with respect to the mean.<br>
The equation of Standard Deviation is:
<center>

$ \sigma = \sqrt{\frac{\Sigma^{N}_{i=1}(x_{i}-\mu)^2}{N}} $
</center>

where $ \sigma$ is the standard deviation of the EMG signal, $ \mu$ is the average of the EMG signal, $ x$ is the value of the EMG signal at the $ i $-th time instant $ N$ is the number of measurements in the EMG signal.
<br><br>

## Minimum 
To choose the best discrimation of the gesture, the minimum value operator which is obtained by searching for the minimum value in the EMG signal.
The equation of minimum is:
<center>

$ X_{min}\ = min_{1 \leq I \leq N}(x_{i})$
</center>
<br><br>

## Maximum
To choose the best discrimation of the gesture, the maximum value operator which is obtained by searching for the maximum value in the EMG signal.
The equation of maximum is:
<center>

$ X_{max}\ = max_{1 \leq I \leq N}(x_{i})$
</center>
<br><br>

## Crossing the zero axis
