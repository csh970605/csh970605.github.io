---
title: Probability and Random Vector
author: SeHoon
date: 2024-04-16 10:02:30 +0900
categories: [Mathmatics, Probability Theory]
tags: [Mathmatics, Kalman Filter]
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
<br><br><br><br>

# Conditional Probability

The probability that event A occurs under a given condition of event B is called the conditional probability of event A. And defines as formula [11].

<p align="center">
    <span>$P(A \mid B) = \frac{P(A,B)}{P(B)}$</span>
    <span style="float: right;">[11]</span>
</p><br>

The conditional probability density function of $X$ ($p_{X\mid Y}(x\mid y)$), given the random variable Y as y, is defined as a relational expression with the condition probability that an event $(X \leq x)$ will occur under the condition $Y=y$, as shown in formula [12]<br>

<p align="center">
    <span>$P(X \leq x \mid Y = y) = \int_{-\infty}^{x} p_{X\mid Y}(x\mid y)dx$</span>
    <span style="float: right;">[12]</span>
</p>

If event A is $(X \leq x)$ and $(Y=y)$ is in the micronet, event B is ($y < Y \leq y+dy$). Therefore, $p_{X\mid Y}(x\mid y)$ is from formula [11] as follow:
<p align="center">
    <span>$p_{X\mid Y}(x\mid y) = \frac{p_{XY}(x, y)}{p_{Y}(y)}, p_{Y} \neq 0$</span>
    <span style="float: right;">[13]</span>
</p>

Else if the probability of event A will occur under the condition $X = x$ is :
<p align="center">
    <span>$p_{X\mid Y}(x\mid y) = \frac{p_{XY}(x, y)}{p_{Y}(y)}, p_{Y} \neq 0$</span>
    <span style="float: right;">[14]</span>
</p>
Opposely, the conditional probability density function of X will occur under the condition event $A$ is:
<p align="center">
    <span>$p_{X|A}(x|A) = \frac{P(A, x)}{P(A)}$</span>
    <span style="float: right;">[15]</span>
</p>

<br><br><br><br>

# Independence Random Variable

If the joint probability of A and B is equal to the product of the probabilities of A and B, then events A and B are called **independent events** :

<p align="center">
    <span>$P(A, B) = P(A)P(B)$</span>
    <span style="float: right;">[16]</span>
</p>

And if the joint probability of the N events $A_{i}, i=1, ... n$ satisfies formula 17, the set is called independent.

<p align="center">
    <span>$P(\bigcap_{i=1}^{n}A_{i}) = \prod_{i=1}^{n}P(A_{i})$</span>
    <span style="float: right;">[17]</span>
</p>

Likewise, if the probability density function of random variable  satisfies formula 18, the N random variables are independent.

<p align="center">
    <span>$p_{X{1},...X_{n}} = \prod_{i=1}^{n}p_{X_{i}}(x_{i})$</span>
    <span style="float: right;">[18]</span>
</p>

If two random variable X and Y are independence, conditional probability density function becomes a function independent of the condition like formula[19].

<p align="center">
    <span>$p_{X\mid Y}(x \mid y) = p_{X}(x)$</span>
    <span style="float: right;">[19]</span>
</p>

<center>

$p_{X\mid Y}(x \mid y) = p_{Y}(y)$
</center>

<br><br><br><br>

# Function of Random Variables

If the random variable Y is givn as a function $Y = g(X)$ of the random variable X , the probability of event $Y \neq y$ is the same as the probability that the random variable X belongs to the real number area ${X \in I_{x}}$ satisfying $g(X) \leq y, so the probability distribution function can be calculated as formula [20].

<center>

$F_{Y}(y) = P(Y \leq y)$
<p align="center">
    <span>$= P(g(X) \leq y)$</span>
    <span style="float: right;">[20]</span>
</p>

$= P(X \in I_{x})$
</center>

For example, let's assume the function relationship between two random variable X and B as $Y = 2X + 3$. Then, the interval of X that satisfies $Y = 2X + 3 \leq y$ is calculated as formula [21].

<center>

$F_{Y}(y) = P(Y \leq y)$
<p align="center">
    <span>$= P(X \leq \frac{y-3}{2})$</span>
    <span style="float: right;">[21]</span>
</p>

$= F_{X}(\frac{y-3}{2})$
</center>

And we can calculate the probability density function of Y as formula [22].
<center>

<p align="center">
    <span>$= P_{Y}(y) = \frac{dF_{Y}(y)}{dy} = \frac{d}{dy}[F_{X}(\frac{y-3}{2})]$</span>
    <span style="float: right;">[22]</span>
</p>

$= F_{X}(\frac{y-3}{2})$
</center>

Of course, calculating the probability density function of two random variables is possible. Let's assume that $Z$ is the sum of two random variables $X$ and $Y$ like: $Z = X + Y$. And, assume again, we know the joint probability density function $p_{XY}(x, y)$ also. Then, $P(Z \leq z)$ equals to $X + Y \leq z$ like:
<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/0077e53e-01cc-493a-bae7-7a1c4c080114">
</center>

Thus, the probability distribution function of $Z$ is formula [23]
<center>

$F_{Z}(z) = P(Z \leq z)$
<p align="center">
    <span>$= P(X+Y \leq z)$</span>
    <span style="float: right;">[23]</span>
</p>

$=\int_{-\infty}^{\infty} \int_{-\infty}^{z-x} p_{XY}(x, y)dydx$
</center>

$\therefore$ The probability density function of $Z$ is formula [24]

<p align="center">
    <span>$p_{Z}(z) = \frac{dF_{Z}(z)}{dz} = \int_{-\infty}^{\infty}\frac{d}{dz}\int_{-\infty}^{z-x}p_{XY}(x,y)dydz$</span>
    <span style="float: right;">[24]</span>
</p>

Next, to solve the formula[24], we use Leibniz interal Rule[28] to become fromula [24].

<p align="center">
    <span>$p_{Z}(z) = \int_{-\infty}^{\infty}p_{XY}(x, z-x)dx$</span>
    <span style="float: right;">[25]</span>
</p>

Like wise, formula [25] can be written like formula [26].

<p align="center">
    <span>$p_{Z}(z) = \int_{-\infty}^{\infty}p_{XY}(z-y,y)dy$</span>
    <span style="float: right;">[26]</span>
</p>

If X and Y are independence, formula[26] become convolution like formula[27].

<center>

$p_{Z}(z)=\int_{-\infty}^{\infty}p_{X}(z-y)p_{Y}(y)dy$
<p align="center">
    <span>$= \int_{-\infty}^{\infty}p_{X}(x)p_{x}(z-x)dx$</span>
    <span style="float: right;">[27]</span>
</p>

$\equiv p_{X}(x) \ast p_{Y}(z)$

</center>

<br><br>

## Leibniz Interal Rule

<p align="center">
    <span>$\frac{d}{dx}\int_{a(x)}^{b(x)}f(x,t)dt = f(x, b(x)){b}'(x)-f(x, a(x)){a}'(x) + \int_{a(x)}^{b(x)} \frac{\partial}{\partial x}f(x, t)dt$</span>
    <span style="float: right;">[28]</span>
</p>




<br><br><br><br>

# Sampling 

The sample that extracted from random variable X whose probability density function is $p_{X}(x)$ is written as follows:

<p align="center">
    <span>$x~p_{X}(x)$</span>
    <span style="float: right;">[29]</span>
</p>

Assume that $N$ number of samples extracted from random variable is {$x^{(1)}, x^{(2)}, ..., x^{(N)}$}, if each samples are extracted independently and fairwisely,the probability of each sample being extracted is the same as formula [30].

<center>

$w_{X}(x^{(i)}) = P(X=x^{(i)})$
<p align="center">
    <span>$=\frac{1}{N}, i = 1, 2, ..., N$</span>
    <span style="float: right;">[30]</span>
</p>


</center>


As in Formula [30], if each sample is independently and equitably extracted from a population with some probabilistic features, the extracted sample is called an **IID(independent and identically distributed) sample**. By using formula[6], it can apporximate $p_{X}(x)$ as follows:

<center>

$p_{X}(x) \approx \Sigma_{N}^{i=1}w_{X}(x^{(i)})\delta (x-x^{(i)})$
<p align="center">
    <span>$=\frac{1}{N}\Sigma_{N}^{i=1} \delta(x-x^{(i)})$</span>
    <span style="float: right;">[31]</span>
</p>
</center>

Then we can calculate the probability $P(x < X \leq x + \Delta x)$ of belonging $X$ to the intever $(x, x+\Delta x]$ as formula [32].

<center>

$\int_{x}^{x+\Delta x}p_{X}(x)dx \approx \int_{x}^{x+\Delta x}\frac{1}{N} \Sigma_{i=1}^{N} \delta (x-x^{(i)})dx$<br>

$=\frac{1}{N}\Sigma_{i=1}^{N} \int_{x}^{x+\Delta x}\delta (x-x^{(i)})$<br>

<p align="center">
    <span>$=\frac{the \ number \ of \ samples \ that \ belongs \ to \ the \ interver (x, x+\Delta x]}{N}$</span>
    <span style="float: right;">[31]</span>
</p>

</center>

<br>

Therefore, the histogram that shows the number of samples belongs to the arbitrary bin has the same shape of the approximation of probability density function $p_{X}(x)$. There is one thing that differ to the probability density function is the area of probability density function must be 1. So, if the area of histogram is normalized to 1, we can get closer shape to the shape of the probability density function.

<br>
<br>

## Example

Question.

---

Assume that $X$ and $Y$ is the independent random variable. And the probability density functions are:
<center>

$p_{X}(x)=\left\{\begin{matrix}
1, \ \ 0\leq x \leq 1\\ 
0, \ \ otherwise
\end{matrix}\right., \ \ \ \ p_{Y}(y)=\left\{\begin{matrix}
1, \ \ 0\leq y \leq 1\\ 
0, \ \ otherwise
\end{matrix}\right.$

$p_{X}(x)=\left\{\begin{matrix}
1, \ \ 0\leq x \leq 1\\ 
0, \ \ otherwise
\end{matrix}\right., \ \ \ \ p_{Y}(y)=\left\{\begin{matrix}
1, \ \ 0\leq y \leq 1\\ 
0, \ \ otherwise
\end{matrix}\right.$

</center>



Get the probability density function of $Z=X+Y$.
<br><br><br><br>

Answer.

---






$p_{Z}(z) = \int_{-\infty}^{\infty}p_{X}(x)p_{Y}(z-x)dx=\int_{0}^{1}p_{X}(z-y)dy$<br>


<!-- $p_{X}(z-y)=\left\{\begin{matrix}
1, \ \ 0\leq z-y \leq 1\\
0, \ \ otherwise
\end{matrix}\right.$ <br> -->


$p_{X}(z-y)=\left\{\begin{matrix}
1\\
0
\end{matrix}\right.$ <br>

$=$
$\left\{\begin{matrix}
1, \ \ z-1\leq y \leq z\\ 
0, \ \ otherwise
\end{matrix}\right.$

Therefore, 
1. $p_{Z}(z)=0, z <0$
2. $p_{Z}(z)= \int_{0}^{z}dx = z, 0 \leq z \leq 1$
3. $p_{Z}(z)= \int_{z-1}^{1}dx = 2-z, 1 < z \leq 2$
4. $p_{Z}(z)= 0, z > 2$