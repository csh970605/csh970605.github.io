---
title: Probability and Random Vector
author: SeHoon
date: 2024-05-07 10:02:30 +0900
categories: [Mathematics, Statistics]
tags: [Mathematics, Statistics, Kalman Filter]
math: true
mermaid: true
---

# Probability
Experiments in which the results are not known in advance are called **random experiments**, although we can predict what is likely to happen. A set of outcomes from a random experiment is called an **event**. A **sample space** is a set of all possible outcomes in a random experiment.<br>
$P(A)$, which means the probability that event $A$ will occur in sample space $S$, is defined by any number that satisfies the 3 axioms:

+ Axiom 1 : Probability is always greater than or equal to 0 ($P(A) \geq 0$).
+ Axiom 2 : The probability of the sample space is 1 ($P(S)=1$).
+ Axiom 3 : In the case of mutually exclusive events A and B, the relationship $P(A \cup B) = P(A) + P(B)$ holds. Mutually exclusive events mean that $A \cap B = \varnothing$, and $\cup$, $\cap$, and $\varnothing$ denote union, intersection, and the empty set, respectively.<br>

Probability is defined by a given case. Therefore, from the three axioms above, we know that $P(\varnothing) = 0$ and $P(A) = 1 - P(\bar{A})$. Here, $\bar{A}$ denotes the complement of event $A$.

<br><br><br><br>

# Random Variable

A random variable $X \equiv X(e)$ is defined as a function that assigns one real number to each element ($e$) in a sample space. A random variable is written in uppercase, and the value that the random variable takes is written in lowercase.

For example, $X(e) = x$ means that the real number corresponding to the random variable in the random experiment is $x$. In short, it can be written as $X = x$.

The domain of a random variable is the sample space, and the range is $-\infty \leq X \leq \infty$, the entire real number line.

Since an event is a set of elements $e$ resulting from a random experiment, there is a corresponding real number interval $I$ for each event $A$. Therefore, if the probability of event $A$ is $P(A)$, the probability that the random variable $X$ belongs to the real number interval $I$ is $P(X \in I) = P(A)$.

Additionally, if a random variable ($X$) takes discrete values, it is called a discrete random variable; if it takes continuous values, it is called a continuous random variable.

<br><br><br><br>

# Probability Distribution Function, Probability Density Function and Probability Mass Function

<br><br>

## Probability Distribution Function

Since $(X \leq x)$ represents an event, it is possible to calculate the probability $P(X \leq x)$ for that event. The probability distribution function of a random variable $X$, denoted $F_{X}(x)$, is defined as $P(X \leq x)$.

The probability distribution function is expressed as follows:
<p align="center">
    <span>$F_{X}(x) = P(X \leq x)$</span>
    <span style="float: right;">[1]</span>
</p>

According to the definition, $F_{X}(-\infty) = 0$ and $F_{X}(\infty) = 1$. Additionally, if $\Delta x \geq 0$, then $F_{X}(x+\Delta x) \geq F_{X}(x)$.
<br><br>

## Probability Density Function

The probability density function $p_{X}(x)$ is defined as a function that satisfies the following equation [2]:

<p align="center">
    <span>$\int_{-\infty}^{x} p_{X}(x)dx = P(X \leq x) = F_{X}(x)$</span>
    <span style="float: right;">[2]</span>
</p>

According to the definition above, if the probability density function is differentiable, it can be expressed as follows:

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

The probability that the random variable $X$ belongs to $(a, b]$ is calculated using the probability density function as follows:

<center>

$P(a < X \leq b) = F_{X}(x \leq b) - F_{X}(x \leq a)$
</center>

<p align="center">
    <span>$= \int^{b}_{a} p_{X}(x)dx$</span>
    <span style="float: right;">[4]</span>
</p>
<br>


According to the definition of the probability density function, $p_{X}(x) \geq 0$ and $\int_{- \infty}^{\infty} p_{X}(x) dx = 1$.

<br><br>

## Probability Mass Function

A discrete random variable $X$ uses a probability mass function $\omega_{X}(x_{i})$ instead of a probability density function.

<p align="center">
    <span>$\omega_{X}(x_{i})=P(X=x_{i}), i= 1, \ldots , n$</span>
    <span style="float: right;">[5]</span>
</p>

where $x_{i}, i = 1, \ldots, n$, represents all elements in the sample space.<br>

By using the Dirac delta function ($\delta(x)$), the probability mass function can be expressed in the form of a probability density function.

<p align="center">
    <span>$p_{X}(x)=\sum^{n}_{i=1}\omega_{X}(x_{i})\delta (x-x_{i})$</span>
    <span style="float: right;">[6]</span>
</p>

Note that the Dirac delta function is defined by the following two properties:

<center>

$\delta (x) = \left\{\begin{matrix}
\infty, x=0\\
0, x\neq 0 

\end{matrix}\right.$ <br>

$\int_{- \infty}^{\infty} \delta(x)dx = 1$
</center>

<br><br><br><br>

# Joint Probability Function 

The **joint probability distribution function** $F_{XY}(x,y)$ of random variables $X$ and $Y$ is defined as the probability of joint events as follows:

<p align="center">
    <span>$F_{XY}(x, y) = P((X \leq x) \cap (Y \leq y))$</span>
    <span style="float: right;">[7]</span>
</p>

<center>

$=P(X \leq x, Y \leq y)$
</center>

The **joint probability density function** $p_{XY}(x, y)$ is derived from the joint probability distribution function as follows:

<p align="center">
    <span>$F_{XY}(x, y) = \int_{-\infty}^{y} \int_{-\infty}^{x} p_{XY}(x, y)dxdy$</span>
    <span style="float: right;">[8]</span>
</p>

If $F_{XY}(x, y)$ is differentiable, the joint probability density function can be expressed as follows:

<p align="center">
    <span>$p_{XY}(x, y) = \frac{\partial^{2}F_{XY}(x, y)}{\partial x \partial y}$</span>
    <span style="float: right;">[9]</span>
</p>

<center>

$=\lim_{\Delta x, \Delta y \rightarrow 0} \frac{P(x < X \leq x + \Delta x, y < Y \leq y+ \Delta y)}{\Delta x \Delta y}$
</center>

Since $F_{X}(x) = F_{XY}(x, \infty)$, the probability density function of $X$ can be obtained using equation [10]. This is called the **marginal density function** of $X$.

<p align="center">
    <span>$p_{X}(x) = \int_{-\infty}^{\infty}p_{XY}(x ,y)dy$</span>
    <span style="float: right;">[10]</span>
</p>
<br><br><br><br>

# Conditional Probability

The probability that an event A occurs given that event B has occurred is called the conditional probability of event A, and it is defined as equation [11].

<p align="center">
    <span>$P(A \mid B) = \frac{P(A,B)}{P(B)}$</span>
    <span style="float: right;">[11]</span>
</p><br>

The [conditional probability](https://csh970605.github.io/posts/Probability_RandomVector/#conditional-probability) density function $p_{X\mid Y}(x\mid y)$ of $X$, given that the random variable $Y$ is $y$, is defined as the probability that the event $(X \leq x)$ will occur given $Y = y$, as shown in equation [12].

<p align="center">
    <span>$P(X \leq x \mid Y = y) = \int_{-\infty}^{x} p_{X\mid Y}(x\mid y)dx$</span>
    <span style="float: right;">[12]</span>
</p>

If event A is $(X \leq x)$ and $Y = y$ is in the infinitesimal interval, then event B is $(y < Y \leq y + dy)$. Therefore, $p_{X\mid Y}(x\mid y)$ is derived from equation [11] as follows:
<p align="center">
    <span>$p_{X\mid Y}(x\mid y) = \frac{p_{XY}(x, y)}{p_{Y}(y)}, p_{Y}(y) \neq 0$</span>
    <span style="float: right;">[13]</span>
</p>

If the probability of event A occurring given that $X = x$ is:
<p align="center">
    <span>$p_{X|A}(a|x) = \frac{P(a, x)}{P_{X}(a)}, p_{X}(x) \neq 0$</span>
    <span style="float: right;">[14]</span>
</p>

Conversely, the conditional probability density function of $X$ given event $A$ is:
<p align="center">
    <span>$p_{X|A}(X|A) = \frac{P(A, x)}{P(A)}$</span>
    <span style="float: right;">[15]</span>
</p>

<br><br><br><br>

# Independent Random Variable

If the joint probability of events A and B equals the product of the probabilities of A and B, then events A and B are called **independent events** :

<p align="center">
    <span>$P(A, B) = P(A)P(B)$</span>
    <span style="float: right;">[16]</span>
</p>

If the joint probability of the N events $A_{i}, i=1, \ldots, n$ satisfies equation [17], the events are called independence.

<p align="center">
    <span>$P(\bigcap_{i=1}^{n}A_{i}) = \prod_{i=1}^{n}P(A_{i})$</span>
    <span style="float: right;">[17]</span>
</p>

Likewise, if the probability density function of random variables satisfies equation [18], the N random variables are independent.

<p align="center">
    <span>$p_{X_{1}, \ldots, X_{n}} = \prod_{i=1}^{n}p_{X_{i}}(x_{i})$</span>
    <span style="float: right;">[18]</span>
</p>

If two random variables $X$ and $Y$ are independent, the conditional probability density function becomes a function independent of the condition, as shown in equation [19].

<p align="center">
    <span>$p_{X\mid Y}(x \mid y) = p_{X}(x)$</span>
    <span style="float: right;">[19]</span>
</p>

<center>

$p_{Y\mid X}(y \mid x) = p_{Y}(y)$
</center>

<br><br><br><br>

# Function of Random Variables

If the random variable $Y$ is given as a function $Y = g(X)$ of the random variable $X$, the probability of the event $Y \leq y$ is the same as the probability that the random variable $X$ belongs to the interval $I_{x}$ satisfying $g(X) \leq y$. Thus, the probability distribution function can be calculated as shown in equation [20].

<center>

$F_{Y}(y) = P(Y \leq y)$
<p align="center">
    <span>$= P(g(X) \leq y)$</span>
    <span style="float: right;">[20]</span>
</p>

$= P(X \in I_{x})$
</center>

For example, let's assume the functional relationship between two random variables $X$ and $Y$ is $Y = 2X + 3$. Then, the interval of $X$ that satisfies $Y \leq 2X + 3$ is calculated as shown in equation [21].

<center>

$F_{Y}(y) = P(Y \leq y)$
<p align="center">
    <span>$= P(X \leq \frac{y-3}{2})$</span>
    <span style="float: right;">[21]</span>
</p>

$= F_{X}(\frac{y-3}{2})$
</center>

The probability density function of $Y$ can be calculated as shown in equation [22].
<center>

<p align="center">
    <span>$P_{Y}(y) = \frac{dF_{Y}(y)}{dy} = \frac{d}{dy}[F_{X}(\frac{y-3}{2})]$</span>
    <span style="float: right;">[22]</span>
</p>

$= \frac{1}{2}p_{X}(\frac{y-3}{2})$
</center>

It is also possible to calculate the probability density function of two random variables. Let's assume that $Z$ is the sum of two random variables $X$ and $Y$: $Z = X + Y$. If we know the joint probability density function $p_{XY}(x, y)$, then $P(Z \leq z)$ is equivalent to $P(X + Y \leq z)$:
<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/0077e53e-01cc-493a-bae7-7a1c4c080114">
</center>

Thus, the probability distribution function of $Z$ is given by equation [23]:
<center>

$F_{Z}(z) = P(Z \leq z)$
<p align="center">
    <span>$= P(X+Y \leq z)$</span>
    <span style="float: right;">[23]</span>
</p>

$=\int_{-\infty}^{\infty} \int_{-\infty}^{z-x} p_{XY}(x, y)dydx$
</center>

$\therefore$ The probability density function of $Z$ is given by equation [24]:

<p align="center">
    <span>$p_{Z}(z) = \frac{dF_{Z}(z)}{dz} = \int_{-\infty}^{\infty}\frac{d}{dz}\int_{-\infty}^{z-x}p_{XY}(x,y)dydz$</span>
    <span style="float: right;">[24]</span>
</p>

Next, to solve equation [24], we use Leibniz integral Rule[28] to become equation [24].

<p align="center">
    <span>$p_{Z}(z) = \int_{-\infty}^{\infty}p_{XY}(x, z-x)dx$</span>
    <span style="float: right;">[25]</span>
</p>

Likewise, equation [25] can be written like equation [26].

<p align="center">
    <span>$p_{Z}(z) = \int_{-\infty}^{\infty}p_{XY}(z-y,y)dy$</span>
    <span style="float: right;">[26]</span>
</p>

If $X$ and $Y$ are independent, equation [26] becomes a convolution as shown in equation [27].

<center>

$p_{Z}(z)=\int_{-\infty}^{\infty}p_{X}(z-y)p_{Y}(y)dy$
<p align="center">
    <span>$= \int_{-\infty}^{\infty}p_{X}(x)p_{X}(z-x)dx$</span>
    <span style="float: right;">[27]</span>
</p>

$\equiv p_{X}(x) \ast p_{Y}(z)$

</center>

<br><br>

## Leibniz Integral Rule

<p align="center">
    <span>$\frac{d}{dx}\int_{a(x)}^{b(x)}f(x,t)dt = f(x, b(x)) \cdot b'(x) - f(x, a(x)) \cdot a'(x) + \int_{a(x)}^{b(x)} \frac{\partial}{\partial x} f(x, t) dt$</span>
    <span style="float: right;">[28]</span>
</p>


<br><br><br><br>

# Sampling 

A sample extracted from the random variable $X$, whose probability density function is $p_{X}(x)$, is written as follows:

<p align="center">
    <span>$x~p_{X}(x)$</span>
    <span style="float: right;">[29]</span>
</p>

Assume that $N$ samples extracted from a random variable are ${x^{(1)}, x^{(2)}, \ldots, x^{(N)}}$. If each sample is extracted independently and fairly, the probability of each sample being extracted is given by equation [30].
<center>

$p_{X}(x) \approx \sum_{i=1}^{N} \omega_{X}(x^{(i)}) \delta (x - x^{(i)})$

<p align="center">
    <span>$=\frac{1}{N}\sum_{i=1}^{N} \delta(x - x^{(i)})$</span>
    <span style="float: right;">[31]</span>
</p>
</center>


As shown in equation [30], if each sample is independently and equitably extracted from a population with some probabilistic features, the extracted sample is called an **IID (independent and identically distributed) sample**. By using equation [6], we can approximate $p_{X}(x)$ as follows:
<center>

$p_{X}(x) \approx \sum_{N}^{i=1}\omega_{X}(x^{(i)})\delta (x-x^{(i)})$
<p align="center">
    <span>$=\frac{1}{N}\sum_{N}^{i=1} \delta(x-x^{(i)})$</span>
    <span style="float: right;">[31]</span>
</p>
</center>

Then we can calculate the probability $P(x < X \leq x + \Delta x)$ of $X$ belonging to the interval $(x, x + \Delta x]$ as shown in equation [32].

<center>

$\int_{x}^{x+\Delta x} p_{X}(x) , dx \approx \int_{x}^{x+\Delta x} \frac{1}{N} \sum_{i=1}^{N} \delta (x - x^{(i)}) , dx$<br>

$=\frac{1}{N} \sum_{i=1}^{N} \int_{x}^{x+\Delta x} \delta (x - x^{(i)}) , dx$<br>

<p align="center">
    <span>$=\frac{\text{the number of samples that belong to the interval } (x, x + \Delta x]}{N}$</span>
    <span style="float: right;">[32]</span>
</p>
</center>

<br>

Therefore, the histogram that shows the number of samples belonging to an arbitrary bin has the same shape as the approximation of the probability density function $p_{X}(x)$. One difference from the probability density function is that the area under the probability density function must be 1. So, if the area of the histogram is normalized to 1, we can obtain a shape closer to that of the probability density function.<br>

For example, let's approximate the probability density function of $Z$ obtained in the  [example](https://csh970605.github.io/posts/Probability_RandomVector/#example) by extracting 10,000 samples each from $X$ and $Y$. The image below shows the probability density function of $Z$ that is approximately calculated using the samples $z^{(i)}$.

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/cf24190c-7fdc-4190-8b2c-b543a48a3044">
</center>

As you can see in the picture above, it merely corresponds to the result of the example.

<br>
<br>

## Example

Question.

---

Assume that $X$ and $Y$ are independent random variables, and their probability density functions are:

<center>
$p_{X}(x)=\left\{\begin{matrix}
1, \ \ 0\leq x \leq 1\\ 
0, \ \ otherwise
\end{matrix}\right., \ \ \ \ p_{Y}(y)=\left\{\begin{matrix}
1, \ \ 0\leq y \leq 1\\ 
0, \ \ otherwise
\end{matrix}\right.$

</center>



Find the probability density function of $Z = X + Y$.
<br><br><br><br>

Answer.

---




<center>


$p_{Z}(z) = \int_{-\infty}^{\infty}p_{X}(x)p_{Y}(z-x)dx=\int_{0}^{1}p_{X}(z-y)dy$<br><br>

$p_{X}(x)=\left\{\begin{matrix}
1, \ \ 0\leq x \leq 1\\ 
0, \ \ otherwise
\end{matrix}\right.$<br>

$=\left\{\begin{matrix}
1, \ \ 0\leq y \leq 1\\ 
0, \ \ otherwise
\end{matrix}\right.$

</center>

Therefore, 
1. $p_{Z}(z)=0, z <0$
2. $p_{Z}(z)= \int_{0}^{z}dx = z, 0 \leq z \leq 1$
3. $p_{Z}(z)= \int_{z-1}^{1}dx = 2-z, 1 < z \leq 2$
4. $p_{Z}(z)= 0, z > 2$

<br><br><br><br>

