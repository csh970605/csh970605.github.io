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

BiomacEMG is a concept suggested by an [article](https://www.mdpi.com/2076-3417/13/9/5744).
<br>
In the article, BiomacEMG classifies seven hand gestures using machine learning. <br>
The gestures are:
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/f644544b-37d5-451e-9e22-cc6a294f813d" width=300 height=500>
</center>
Let's now see how it works.
<br><br><br><br>


# What is EMG?

EMG (electromyography) is a type of physiological signal recording that detects electrical signals from muscle fibers in response to gestures or movements.<br>

<br><br><br><br>

# What does BiomacEMG do?

The article uses surface electrodes to collect electromyographic (EMG) data from the forearm flexion and extension muscles, which are used as input parameters for the machine learning algorithms to recognize seven hand gestures.<br>

Since EMG signals are erratic, signal analysis performance is generally poor. They measure different types of muscle groups in real time, which are:

+ The flexor carpi radialis muscle is responsible for the flexion and radial deviation of the wrist.<br>

+ The flexor pollicis longus muscle, which is responsible for the flexion of the thumb.<br>

+ The flexor digitorum muscle, which is responsible for the flexion of the fingers.<br>

+ The flexor carpi ulnaris muscle, which is responsible for the flexion and ulnar deviation of the wrist.<br>

+ The extensor pollicis longus and brevis muscles, which are responsible for the extension of the thumb.<br>

+ The extensor carpi ulnaris muscle is responsible for the extension and ulnar deviation of the wrist.<br>

+ The extensor digitorum muscle, which is responsible for the extension of the fingers.<br>

+ The extensor carpi radialis muscle, which is responsible for the extension and radial deviation of the wrist.<br>

You can see which muscles are used in the pictures below:
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/39c46a76-ef03-45ee-8885-10b1a8f93e85" width="330" height="300"><img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/a54f1c86-ba1e-4ce2-ae9d-18bc0cc83bef" width="350" height="300">
</center>
<br><br>
<br><br>

# Steps of Classifying Gestures

1. Feature extraction<br>
    In this article, nine features were extracted, which are:

    + [Standard deviation](https://csh970605.github.io/posts/BiomacEMG/#standard-deviation)

    + [Minimum](https://csh970605.github.io/posts/BiomacEMG/#minimum)

    + [Maximum](https://csh970605.github.io/posts/BiomacEMG/#maximum)

    + [Crossing the zero axis](https://csh970605.github.io/posts/BiomacEMG/#crossing-the-zero-axis)

    + [Average change in amplitude](https://csh970605.github.io/posts/BiomacEMG/#average-change-in-amplitude)

    + [The first amplitude jump](https://csh970605.github.io/posts/BiomacEMG/#the-first-amplitude-jump)

    + [Mean absolute value](https://csh970605.github.io/posts/BiomacEMG/#mean-absolute-value)

    + [Wave length](https://csh970605.github.io/posts/BiomacEMG/#wave-length)

    + [Wilson amplitude](https://csh970605.github.io/posts/BiomacEMG/#wilson-amplitude)

    You can see how the methods are used by clicking the link for each method.

2. [PCA](https://csh970605.github.io/posts/PCA/)<br>
    PCA showed that gesture classes overlap strongly in the feature space.

3. [Random Forest Classification](https://csh970605.github.io/posts/Random_Forest_Classification/)<br>
    Since the signal data is non-linear, they chose Random Forest Classification, a non-linear classification method.

4. [Pareto Optimization](https://csh970605.github.io/posts/Pareto_Front/)<br>
    In the context of EMG feature selection, Pareto optimization is used to identify the optimal subset of EMG features that best represent the underlying signal while minimizing the number of features required for classification. <br>
    To do this, a Pareto front is first constructed by generating multiple solutions that represent different trade-offs between performance and the number of features. <br>
    Each solution is evaluated on the basis of its classification accuracy and the number of features it employs. <br>
    The set of all solutions that cannot be improved in one objective without sacrificing performance in another is called the Pareto front.

<br><br>

## Standard Deviation
Standard deviation is a measure of absolute variability that shows how individual
observations are grouped with respect to the mean.<br>
The equation for the standard deviation is:
<center>

$ \sigma = \sqrt{\frac{\sum^{N}_{i=1}(x_{i}-\mu)^2}{N}} $
</center>

where $ \sigma$ is the standard deviation of the EMG signal, $ \mu$ is the average of the EMG signal, $ x$ is the value of the EMG signal at the $ i $-th time instant $ N$ is the number of measurements in the EMG signal.
<br><br>

## Minimum 
To choose the best discrimination of the gesture, the minimum value operator is obtained by searching for the minimum value in the EMG signal.
The equation for the minimum is:
<center>

$ X_{min}\ = \min_{1 \leq i \leq N}(x_{i})$
</center>
<br><br>

## Maximum
To choose the best discrimation of the gesture, the maximum value operator which is obtained by searching for the maximum value in the EMG signal.
The equation of maximum is:
<center>

$ X_{max}\ = \max_{1 \leq i \leq N}(x_{i})$
</center>
<br><br>

## Crossing the zero axis

Crossing the zero axis is a convenient and fast way to estimate the frequency of a sampled sequence of data. A zero crossing is the point where the sign of a function inverts to its opposite. It is a signal evaluation indicator often employed in electronics, mathematics, acoustics, and image processing. The equation for zero crossing is:
<center>

$ s(x,y) \ = \ \left\{\begin{matrix}
1 \ \ \ if(xy) < 0
\\ 
0 \ \ \ if(xy) > 0
\end{matrix}\right.$

$ZC(V) = \sum^{n-1}_{i=1}s(V_i, V_{i+1})$
<br>
where $ZC$ is the zero crossing value, and $x$ and $y$ are the EMG signal values.
</center>
<br><br>

## Average change in amplitude
The average amplitude is the average magnitude of all instantaneous values in the
EMG time signal.<br>
The equation for the average change is:
<center>

$i_{Avg} \ = \ \frac{1}{N}\sum^{N}_{i=1}x_i$<br>
where $x$ = amplitude value
</center>
<br><br>

## The first amplitude jump
The first amplitude jump refers to the first major change or increase that occurs at a specific point in time.

<br><br>

## Mean absolute value(MAV)
Mean absolute deviation, also known as mean absolute error, is a measure of the accuracy of a forecasting method, such as trend estimation, and is also used as a loss function. MAV is a method to determine and evaluate the level of muscle contraction. The equation for MAV is:

<center>

$MAV \ = \ \frac{1}{N}\left | x_{i} \right |$
</center>

<br><br>

## Wave length
Wave length is intuitively the total length of the waveform in a segment.<br>
The resulting waveform length values provide a measure of the amplitude, frequency, and duration of the waveform. The equation for the waveform length is:
<center>

$WL = \sum^{N-1}_{i=1}\left | x_{i+1} \ - \ x_{i}  \right |$
</center>
<br><br>

## Wilson amplitude(WAMP)
WAMP is the number of times the difference between the amplitudes of the sEMG signal in two adjacent segments exceeds a predetermined threshold to reduce the effects of noise. WAMP is related to the level of motor unit action potential (MUAP) and muscle contraction. A suitable value for the threshold parameter is
usually chosen between 10 and 100 mV, which depends on the gain setting of the instrument.<br>
<center>

$WAMP \ = \ \sum^{N-1}_{i=1}f(\left | x_{i} \ - \ x_{i+1}  \right |)$<br>

$f(x) \ = \ \left\{\begin{matrix}
1 \ \ \ \text{if}(x \geq y)
\\ 
0 \ \ \ \text{otherwise}
\end{matrix}\right.$
</center>

<br><br><br><br>

# Result
Each contraction of the arm muscles during one of the seven movements was recorded by eight EMG sensors. The result of each methods:
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/07a4a9f4-a672-4e7c-876c-b6009f5621cd" width=500 height=500>
</center><br>

And also, the minimum, mean, and maximum values of the gesture features are summarized in table below:

<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/50c294f7-b838-41c4-a264-49c64dc4b243">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/0760a9b8-8b9f-4693-958b-505be607ff06">
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/5942d5ee-2690-4b8c-ad01-8414deff5a22">
</center><br>

Through PCA, distinguishable data consisting of P1, P2, and P3 can be obtained which is:
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/4925d84b-d3fd-464a-a043-0d2226cef647" width=600 height=500>

</center>
<br>

At the end, we can see the classification result with random forest classifier.
<center>
<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/566b56d8-4683-459e-8baf-0a3ba32a9d5b">
</center>

<br><br><br><br>

# Opinion

In the article, they stated the accuracy is 92%, but by simple calculation, the accuracy appears to be 84%.<br>
Unlike other studies that used deep learning techniques such as RNN or CNN, they only used machine learning.<br>
However, it may be the fastest way to classify hand gestures. I also want to know the performance of other hand gestures when used in real-life applications.