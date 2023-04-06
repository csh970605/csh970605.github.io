---
title: Thompson Sampling
author: SeHoon
date: 2023-04-06 14:42:30 +0900
categories: [Machine Learning, ML_Theory]
tags: [machine learning, python]
math: true
mermaid: true
---

# What is Thompson Sampling?
Unlike [UCB](https://csh970605.github.io/posts/UCB/), which selects a high confidence interval, Thompson samling creates a probabilistic perception.
<br><br>

## Algorithm of Thompson Sampling
---
<br>
Let's assume that we are planning an advertisement.<br>
There are 3 steps to get the result:

+ Step 1. <br>
At each round n, we consider two numbers for each ad *i*:
    + $N_{i}^{1}(n)$ : the number of times the ad *i* got reward 1 up to round *n*.
    + $N_{i}^{0}(n)$ : the number of times the ad *i* got reward 0 up to round *n*.<br><br>

+ Step 2.<br>
For each ad *i*, we take a random draw from the distribution below:
<br>

<center>
<font size=4>

$\theta_{i}(n) = \beta(N_{i}^{1}(n)\ +\ 1,\ N_{i}^{0}(n)\ +\ 1)$
</font>
</center>
<br>

+ Step 3.<br>
Select the ad that has the highest $\theta_{i}(n).$


## The process of deriving the result value of Thompson Sampling
---
<br>

You can see the graph. X axis means that we expected profit from ad. And the bar means center of distribution.
<center>
<img src="https://user-images.githubusercontent.com/28240052/230351720-264315ab-d644-4e2d-a563-187d1c46c4db.png" width=500>
</center>
<br><br>
After that, Let's assume we try a round to blue ad and get the result like:<br>
 
<center>
<img src="https://user-images.githubusercontent.com/28240052/230354187-d6eb6ea8-d0e3-45c6-b68f-ec53c8076042.png" width=500>
</center>
<br><br>
Thompson Sampling creates a new distribution by incorporating the results into a distribution.
<center>
<img src="https://user-images.githubusercontent.com/28240052/230354437-56464645-5b6b-4f5e-8ac5-06f342e6d5af.png" width=500>
</center>
<br><br>
As above, apply it to yellow ad and blue ad and get the result.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/230354668-3d3b3ac1-ea84-4c4a-b9b5-9249200494f0.png" width=500>
</center>
<br><br>

As you can see, the expected value which machine produces does not match the actual distribution.<br>
To solve this problem, we can help machine by giving real expected value.<br>
And the distribution will be change like:
<center>
<img src="https://user-images.githubusercontent.com/28240052/230355627-5fa889b5-8c5f-4d44-adc6-92bee7a873b0.png" width=500>
</center>
<br><br>
Repeat the above process until the distribution created by the machine is sufficiently refined.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/230355895-288b5576-4eee-4e43-b7bf-bf73c6ad26fc.png" width=500>
</center>
<br><br>

As you can see in the image above, yellow ad will gives us the highest profit.
<br><br><Br>

# Example
<br><br>

## Code
---
<br>

```py
import random

N = 10000
d =10
ads_selected =[]
numbers_of_reward_1 = [0] * d
numbers_of_reward_0 = [0] * d
total_reward = 0
for n in range(N):
  ad = 0
  max_random = 0
  for i in range(d):
    # Step 2
    random_beta = random.betavariate(numbers_of_reward_1[i] + 1, numbers_of_reward_0[i] + 1)
    # Step 3
    if random_beta > max_random:
      max_random = random_beta
      ad = i
  ads_selected.append(ad)
  reward = dataset.values[n, ad]
  if reward == 1:
    numbers_of_reward_1[ad] += 1
  elif reward == 0:
    numbers_of_reward_0[ad] += 1
  total_reward += reward


plt.hist(ads_selected)
plt.title('Histogram of ads selections')
plt.xlabel('Ads')
plt.ylabel('Number of times each ad was selected')
plt.show()
     
```
<br><br>

## Result
---
<br>

<center>
<img src="https://user-images.githubusercontent.com/28240052/230357230-206603b6-3e33-4b74-8954-f218161cc163.png">
</center>
<br><br>