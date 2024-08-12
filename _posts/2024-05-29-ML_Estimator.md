---
title: ML Estimator
author: SeHoon
date: 2024-05-22 09:03:30 +0900
categories: [Mathematics, Estimator]
tags: [Mathematics, Statistics, Kalman Filter, Estimator]
math: true
mermaid: true
---

# ML(Maximum Likelihood) Estimator

Since the ML Estimator is a [non-Bayesian estimator](https://csh970605.github.io/posts/Static_Estimate/#non-bayesian-approach), it considers the vector $X$ as an unknown fixed value. Thus, it should be noted that $X$ is not a[random vector](https://csh970605.github.io/posts/Rand_Vector/).<br>

Since the measurement vector $z$ varies depending on the value of $x$, the [probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#probability-density-function) of $Z$ is a function of the unkown vector $x$. This is expressed as $p_{Z}(z(x))$.<br>

Additionally, the [joint probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#joint-probability-function) of the measurement vector union is written as $p_{Z_{k}}(z_{k}(x))$.<br>

An ML estimator is defined as an estimate that maximizes the joint probability density function of $Z_{k}$. That is, $\hat{x}^{ML} = \text{argmax} p_{Z_{k}}(z_{k}(x))$. Since it is similar to the [MAP Estimator](https://csh970605.github.io/posts/MAP_Estimator/), to maintain consistency in notation, it is common to express $p_{Z_{k}}(z_{k}(x))$ as a [conditional probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#conditional-probability) as:

<center>

$\hat{x}^{ML} = \text{argmax} p_{Z_{k}\mid X}(z_{k}\mid x)$
</center>

