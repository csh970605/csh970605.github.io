---
title: Probability and Random Vector
author: SeHoon
date: 2024-04-16 10:02:30 +0900
categories: [Mathmatics, Probabilitics]
tags: [Mathmatics MultiObjectTracking]
math: true
mermaid: true
---

# Probability
Experiments in which the results are not known in advance are called **random experiments**, although we can all know what are likely to happen. And a set of outcomes from a random experiment is called **event**. And a **sample space** is a set of all possible outcomes in a random experiment.<br>
$P(A)$, which means the probability that event $A$ will occur in sample space $S$, is defined by any number that satisfies the 3 axioms:

+ Axiom 1 : Probability is also bigger or equal than 0($P(A) \geq 0$).
+ Axiom 2 : Probability of sample space is 1($P(S)=1).
+ Axiom 3 : In the case of mutually exclusive events A and B, the relational expression of $P(A \cup B)=P(A)+P(B)$ is established. Where mutually exclusive events mean that $A \cap B = \varnothing$ and $\cup, \cap$ and $\varnothing$ means union, intersectionand empty respectively.<br>

Probability defined by a given case. Therefore, from 3 axioms above, we can know  $P(\varnothing)=0, P(A)=1-P(\bar{A})$ is established. Where $\bar{A}$ means that it is complementary event of $A$.

<br><br><br><br>

# Random Variable

Random variable $X\equiv X(e)$ is defined as a function that corresponds to one real number to each element($e$) constituting a sample space. Random variable is written in upper case and the value that random variable will actually take is written in lower case.

e.g. $X(e)=x$ means that the real number of the random variable corresponding to the random experience is x. In short, it can be written as $X=x$.

The domain of random variable is sample space and the range is $-\infty \leq X \leq \infty$, the whole real number area.

Since an event is a set of $e$ as an element, which is the result of random experiment, there is a corresponding real number interver $I$ for each event $A$. Therefore, if the probability of event A is $P(A)$, the probability that random variable $X$ of belonging to the real number interver is $P(X \in I) = P(A)$.

And also, if random variable($X$) takes a discrete value, it is called a discrete random varaible, if it takes a continous value, it is called a continuous random variable.

<br><br><br><br>

# Probability Distribution Function, Probability Density Function and Probability Mass Function

<br><br>

## Probability Distribution Function

Since $(X \leq x)$ means an event, calculating the probability $P(X \leq x)$ for that event is possible. The probability distribution function of random variable $X$ ($F_{X}(x)$) is defined as $P(X \leq x)$.

The state-space equation is expressed as follows:
<p align="center">
    <span>$\therefore F_{X}(x) = P(X \leq x)$</span>
    <span style="float: right;">[1]</span>
</p>

According to the definition, $F_{X}(-\infty) = 0, F_{X}(\infty) = 1$. Also, if $\Delta x \geq 0$, $F_{X}(x+\Delta x) \geq F_{X}(x)$.

<br><br>

## Probability Density Function

The probability density function of $p_{X}(x)$ defines the following integral expression[2] as a function that satisfies.

<p align="center">
    <span>$\int_{-\infty}^{x} p_{X}(x)dx = P(X \leq x) = F_{X}(x)$</span>
    <span style="float: right;">[2]</span>
</p>

According to the definition above, if probability density function can be differntiated, probability density function can be expressed as follows:

<center>

$p_{X}(x) = \frac{dF_{X}(x)}{dx}$
</center>

<p align="center">
    <span>$= \lim_{\Delta x \rightarrow 0} \frac{F_{X}(x+\Delta x) - F_{X}(x)}{\Delta x}$</span>
    <span style="float: right;">[3]</span>
</p>

<center>

$= \lim_{\Delta x \rightarrow 0} \frac{P(x < X \leq x + \Delta x)}{\Delta x}$
</center>

The probability that random variable $X$ belongs to $(a, b])$ is calculated by using probability density function as follows:

<center>

$P(a < X \leq b) = F_{X}(X \leq b) - F_{X}(X \leq a)$
</center>

<p align="center">
    <span>$= \int^{b}_{a} p_{X}(x)dx$</span>
    <span style="float: right;">[4]</span>
</p>
<br>


According to the definition of probability density function,$p_{X}(x) \geq 0, \int_{- \infty}^{\infty} p_{X}(x)dx=1$.

<br><br>

## Probability Mass Function

At the discrete random variable $X$ uses probability mass function $w_{X}(x_{i})$ instead of probability density function.

<p align="center">
    <span>$w_{X}(x_{i})=P(X=x_{i}), i= 1, ..., n$</span>
    <span style="float: right;">[5]</span>
</p>

where $x_{i}, i = 1, ..., n$ is all elements in sample space.<br>

If you use Dirac delta function ($\delta(x)$), you can express probability mass function to the form of probability density function.

<p align="center">
    <span>$p_{X}(x)=\Sigma^{n}_{i=1}w_{X}(x_{i})\delta (x-x_{i})$</span>
    <span style="float: right;">[6]</span>
</p>

Note that Dirac delta function is defined as a function that satifies two properties as follows:

<center>

$\delta (x) = \left\{\begin{matrix}
\infty, x=0\\
0, x\neq 0 

\end{matrix}\right.$<br>

$\int_{- \infty}^{\infty} \delta(x)dx = 1$
</center>

<br><br><br><br>

# Joint Probability Function 

**Joint probability distribution function** of random variable $X$ and $Y$ ($F_{XY}(x,y)$) is defined as probability of joint event as follows:

<p align="center">
    <span>$F_{XY}(x, y) = P((X \leq x) \cap (Y \leq y))$</span>
    <span style="float: right;">[7]</span>
</p>

<center>

$=P(X \leq x, Y \leq y)$
</center>

**Joint probability density function** ($p_{XY}(x, y)$) is defined from the joint probability distribution function as follows:

<p align="center">
    <span>$F_{XY}(x, y) = \int_{-\infty}^{y} \int_{-\infty}^{x} p_{XY}(x, y)dxdy$</span>
    <span style="float: right;">[8]</span>
</p>

if $F_{XY}(x, y)$ can be differentiated, joint probability density function can be expressed as follows:

<p align="center">
    <span>$p_{XY}(x, y) = frac{\partial^{2}F_{XY}(x, y)}{\partial x \partial y}$</span>
    <span style="float: right;">[9]</span>
</p>

<center>

$=\lim_{\Delta x, \Delta y \rightarrow} \frac{P(x < X \leq x + \Delta x, y < Y \leq y+ \Delta y)}{\Delta x \Delta y}$
</center>

Since $F_{X}(x) = F_{XY}(x, \infty)$ is True, you can get the probability density function of only X by formula[10]. It is called **marginal density function** of X.

<p align="center">
    <span>$p_{X}(x) = \int_{-\infty}^{infty}p_{XY}(x ,y)dy$</span>
    <span style="float: right;">[10]</span>
</p>

# Conditional Probability

The probability that event A occurs under a given condition of event B is called the conditional probability of event A. And defines as formula [11].

<p align="center">
    <span>$P(A|B) = \frac{P(A,B)}{P(B)}$</span>
    <span style="float: right;">[11]</span>
</p>


The conditional probability density function of $X$ 

<p align="center">
    <span>$P(X \leq x | Y = y) = \int_{-\infty}^{x} p_{X|Y}(x|y)dx$</span>
    <span style="float: right;">[12]</span>
</p>
