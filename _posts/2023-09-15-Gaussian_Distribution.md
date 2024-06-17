---
title: Gaussian Distribution
author: SeHoon
date: 2023-09-15 10:42:30 +0900
categories: [Mathematics, Statistics]
tags: [Mathematics, Statistics]
math: true
mermaid: true
---

# Gaussian Distribution

The Gaussian distribution, also known as the normal distribution, is a type of continuous probability distribution. The general form of its [probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#probability-density-function) is :

<center>

$f(x) = \frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{1}{2}(\frac{x-\mu}{\sigma})^2}$<br>

</center>

where <br>

+ $\mu$ : The mean or expectation of the distribution.<br>
+ $\sigma$ : The standard deviation.


Since the Gaussian distribution is characterized by two parameters, the mean and the standard deviation, it is easy to treat mathematically. Additionally, since many natural signals are similar to the Gaussian distribution, it is often used to model various social and natural phenomena.

The shape of the Gaussian distribution is:

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/04a3e688-62ca-45e3-b253-73717f7bb95d">
</center>

<br><br><br><br>


# Gaussian Random Vector

The probability density function of a Gaussian [random vector](https://csh970605.github.io/posts/Rand_Vector/) $X$ is defined as in formula [1].

<center>

$p_{X}(x) = N(x \mid \mu_{X}, P_{XX})$

<p align="center">
    <span>$= \frac{1}{\sqrt{(2 \pi)^{n}detP_{XX}}}e^{-\frac{1}{2}(x-\mu_{X})^{T}P_{XX}^{-1}(x-\mu_{X})}$</span>
    <span style="float: right;">[1]</span>
</p>

</center>

where

+ $\mu_{X}$ : Expectation.
+ $P_{XX}$ : Covariance.
+ $n$ : Dimension of $X$.
+ $detP_{XX}$ : determinant of $P_{XX}$.

The Gaussian random variable $X$ is expressed simply as $X \sim N(x \mid \mu, \sigma^{2})$, and the Gaussian random vector $X$ is expressed simply as $X \sim N(X \mid \mu_{X}, P_{XX})$.

Below are images that show the shape of the 2-dimensional Gaussian probability density function with different means and covariances:

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/ed93ccbd-8629-401e-9dee-46c4556217d0">

$\mu_{X} = \begin{bmatrix}
0 & 0
\end{bmatrix}^{T}, \ P_{XX} = \begin{bmatrix}
1 & 0\\ 
0 & 1
\end{bmatrix}$

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/8dc73f2b-7a9b-4b58-b910-86bba9ab2638">

$\mu_{X} = \begin{bmatrix}
2 & 2
\end{bmatrix}^{T}, \ P_{XX} = \begin{bmatrix}
1 & 0\\ 
0 & 1
\end{bmatrix}$


<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/fda429eb-b433-497c-802a-06371666d645">

$\mu_{X} = \begin{bmatrix}
0 & 0
\end{bmatrix}^{T}, \ P_{XX} = \begin{bmatrix}
1 & 0.5\\ 
0.5 & 1
\end{bmatrix}$


<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/6992fa4d-4f04-4160-bac1-935ce0dcebf8">

$\mu_{X} = \begin{bmatrix}
0 & 0
\end{bmatrix}^{T}, \ P_{XX} = \begin{bmatrix}
1 & -0.5\\ 
-0.5 & 2
\end{bmatrix}$

</center>

According to the images above, if the values of the off-diagonal terms are 0, the contour is a circle around the mean, and if the values of the off-diagonal terms are not 0, the contour is an ellipse around the mean. You can see the proof [here](https://csh970605.github.io/posts/Gaussian_Distribution/#proof-1).

<br><br>

## Joint Gaussian Random Vector

If the random vector $Y = \begin{bmatrix} 
X \ 
Z 
\end{bmatrix}$ that consists of random vectors $X$ and $Z$ has a Gaussian distribution, it is called a **joint Gaussian random vector**. The probability density function is:

<center>

$p_{XZ}(x, z) = p_{Y}(y) = N(y\mid \mu_{Y}, P_{YY})$
</center>

The expectation and the covariance of $Y$ can be expressed using the expectation and the covariance of $X$ and $Z$ as follows:

<center>

$\mu_{Y} = \begin{bmatrix}
\mu_{X} \\
\mu_{Z}
\end{bmatrix}, P_{YY} = \begin{bmatrix}
P_{XX} & P_{XZ}\\
P_{ZX} & P_{ZZ}
\end{bmatrix}$
</center>

Where

+ $P_{XX}$ : $\mathbb{E}[(X - \mu_{X})(X-\mu_{X})^{T}]$

+ $P_{ZZ}$ : $\mathbb{E}[(Z - \mu_{Z})(Z-\mu_{Z})^{T}]$

+ $P_{XZ}$ : $\mathbb{E}[(X - \mu_{X})(Z-\mu_{Z})^{T}]$

+ $P_{ZX}$ : $\mathbb{E}[(Z - \mu_{Z})(X-\mu_{X})^{T}]$

<br><br>

## Feature of Gaussian Random Vector

There are 5 features of a Gaussian random vector.

1. The linear transform of a Gaussian random vector is a Gaussian random vector.

2. If random vectors $X$ and $Z$ have a joint Gaussian distribution, $X$ and $Z$ are Gaussian random vectors respectively. That is, if $p_{XZ}(x, z) = p_{Y}(y)=N(y \mid \mu_{Y}, P_{YY})$,<br>
$=X \sim N(z \mid A\mu_{X}, AP_{XX}A^{T})$.

3. Non-correlated Gaussian random vectors are independent of each other.

4. If two Gaussian random vectors $X$ and $Z$ are independent of each other, the sum of the two vectors is a Gaussian random vector. That is, if $X \sim N(x \mid \mu_{X}, P_{XX})$, $Z \sim N(z \mid \mu_{Z}, P_{ZZ})$,<br>
$=X + Z \sim N(\mu_{X} + \mu_{Z}, P_{XX} + P_{ZZ})$

5. If two random vectors $X$ and $Z$ has joint gaussian distribution, the [conditional probability](https://csh970605.github.io/posts/Probability_RandomVector/#conditional-probability) density function of $X$ or $Z$ is gaussian too.
<br>

You can see the proofs of these five features here: [1](https://csh970605.github.io/posts/Gaussian_Distribution/#proof-2), [2](https://csh970605.github.io/posts/Gaussian_Distribution/#proof-3), [3](https://csh970605.github.io/posts/Gaussian_Distribution/#proof-4), [4](https://csh970605.github.io/posts/Gaussian_Distribution/#proof-5), [5](https://csh970605.github.io/posts/Gaussian_Distribution/#proof-6)
<br><br><br><br>


# Characteristic Function of Gaussian Random Vector

The [characteristic function](https://csh970605.github.io/posts/Rand_Vector/#characteristic-function) of random vector $N(x \mid \mu_{X}, P_{XX})$ is:

<center>

$\Phi_{X}(\omega) = e^{j\omega^{T} \mu_{X} - \frac{1}{2} \omega^{T}P_{XX}\omega}$

</center>


<br><br><br><br>


# Proof

<br><br>

## Proof 1.

Show that given the expected value of Gaussian random vector $X=\begin{bmatrix}
X_{1} & X_{2}
\end{bmatrix}^{T}$ as $\mu_{X}$ and the covariance matrix as $P_{XX}$, the contour is an ellipse centered around $\mu_{X}$.
<br><br>

---

The formula of the contour that the value of probability density function is $c_{1}$ follows as:

<center>

$p_{X}(X) = \frac{1}{\sqrt{(2 \pi)^{n}detP_{XX}}}e^{-\frac{1}{2}(x-\mu_{X})^{T}P_{XX}^{-1}(x-\mu_{X})}$
</center>

Since all values except $X$ are constant, the formula above can be written as:

<center>

$(x-\mu_{X})^{T}P_{XX}^{-1}(x-\mu_{X})=c_{2} > 0$
</center>

where $c_{2}$ is a constant.

Because $P_{XX}$ is a positive-definite matrix, it has eigenvalues $\lambda_{1}, \lambda_{2}$ which are greater than 0, and eigenvectors $v_{1}, v_{2}$ which are orthogonal. Thus, we can decompose $P_{XX}$ as:

<center>

$P_{XX} = \mathbb{E}\wedge \mathbb{E}_{T}$
</center>

where

+ $\mathbb{E}$ : $\begin{bmatrix}
v_{1} & v_{2}
\end{bmatrix}$

+ $\wedge$ : $diag(\lambda_{1}, \lambda_{2})$

+ $\mathbb{E}^{T}\mathbb{E}$ : $I$


Since $P_{XX}^{-1} = \mathbb{E} \wedge^{-1} \mathbb{E}^{T}$ accordingly, let $y = \mathbb{E}^{T}(X- \mu_{X})$. Then, the formula $(x-\mu_{X})^{T}P_{XX}^{-1}(x-\mu_{X})$ becomes:

<center>

$(x-\mu_{X})^{T}P_{XX}^{-1}(x-\mu_{X}) = (x-\mu_{X})^{T}\mathbb{E} \wedge^{-1} \mathbb{E}^{T}(X-\mu_{X})$

$= y^{T}\wedge^{-1}y$

$= \frac{y_{1}^{2}}{\lambda_{1}} + \frac{y_{2}^{2}}{\lambda_{2}} $

$= c_{2}$
</center>

where $y=\begin{bmatrix}
y_{1} & y_{2}
\end{bmatrix}^{T}$.

So, the contour of the Gaussian probability density function is an ellipse centered around $\mu_{X}$. The lengths of the main axes are $\sqrt{\lambda_{1}}$ and $\sqrt{\lambda_{2}}$, and the directions of the main axes are $v_{1}$ and $v_{2}$ respectively.

<br><br>

## Proof 2.

Prove the first feature of a Gaussian random vector.
<br><br>

---

Let the random vector $Y$ be the linear transform of the Gaussian random vector $X$. Then, check the characteristic function of the random vector $Y$.<br>

<center>

$\Phi_{Y}(\omega) = \mathbb{E}[e^{jw^{T}Y}] = \mathbb{E}[e^{jw^{T}AX}]$

$=\Phi_{X}(A^{T}\omega)$

$= e^{j\omega^{T}A\mu_{X}-\frac{1}{2}\omega^{T}AP_{XX}A^{T}\omega}$

$\therefore Y = AX \sim N(y \mid A\mu_{X}, AP_{XX}A^{T})$
</center>

<br><br>

## Proof 3.

Prove the second feature of a Gaussian random vector.
<br><br>

---

Let $Y= \begin{bmatrix} 
X \\ 
Z 
\end{bmatrix}$, where $X$ and $Z$ are random vectors respectively.<br>

Then, $X=\begin{bmatrix}
I & 0
\end{bmatrix}, \begin{bmatrix}
X \\
Z
\end{bmatrix} = \begin{bmatrix}
I & 0
\end{bmatrix}Y$.

Therefore, according to the [first feature of Gaussian random vector](https://csh970605.github.io/posts/Gaussian_Distribution/#proof-2), $X$ must be a Gaussian vector.

In detail, the expectation and covariance of $X$ are:

<center>

$\mathbb{E}[X] = \begin{bmatrix}
I & 0
\end{bmatrix}\mu_{Y} = \begin{bmatrix}
I & 0
\end{bmatrix}\begin{bmatrix}
\mu_{X} \\
\mu_{Z}
\end{bmatrix} = \mu_{X}$

$Cov(X) = \begin{bmatrix}
I & 0
\end{bmatrix}P_{XX}\begin{bmatrix}
I \\
0
\end{bmatrix} = \begin{bmatrix}
I & 0
\end{bmatrix} \begin{bmatrix}
P_{XX} & P_{XZ} \\
P_{ZX} & P_{ZZ}
\end{bmatrix} \begin{bmatrix}
I \\
0
\end{bmatrix} = P_{XX}$
</center>
<br><br>

## Proof 4.

Prove the third feature of a Gaussian random vector.
<br><br>

---

Let there be two Gaussian random vectors $X \sim N(\mu_{X}, P_{XX})$ and $Z \sim N(\mu_{Z}, P_{ZZ})$. If $X$ and $Z$ are non-correlated, then $P_{XZ} = P_{ZX} = 0$ because $\mathbb{E}[(X-\mu_{X})(Z-\mu_{Z})^{T}] = \mathbb{E}[(Z-\mu_{Z})(X-\mu_{X})^{T}] = 0$.

Then, the covariance of joint gaussian random vector is:
<center>

$P_{YY} = \begin{bmatrix}
P_{XX} & 0 \\
0 & P_{ZZ}
\end{bmatrix}$

$\therefore P_{YY}^{-1} = \begin{bmatrix}
P_{XX}^{-1} & 0 \\
0 & P_{ZZ}^{-1}
\end{bmatrix}, detP_{YY} = detP_{XX}detP_{ZZ}$
</center>

Finally,
<center>

$p_{XZ}(x, z) = p_{Y}(y) = N(y \mid \mu_{Y}, P_{YY})$

$= N(x \mid \mu_{X}, P_{XX})N(z \mid \mu_{Z}, P_{ZZ})$

$= p_{X}(x)p_{Z}(z)$
</center>

So, $X$ and $Z$ are independent of each other.

<br><br>

## Proof 5.

Prove the fourth feature of a Gaussian random vector.
<br><br>

---

Let the sum of two independent random variables $X$ and $Z$ be $Y$. Then, the characteristic function of $Y$ is:

<center>

$\Phi_{Y}(\omega) = \mathbb{E}[e^{jw^{T}Y}] = \mathbb{E}[e^{jw^{T}(X+Z)}] = \mathbb{E}[e^{jw^{T}X}e^{jw^{T}Z}]$

$=\mathbb{E}[e^{jw^{T}X}]\mathbb{E}[e^{jw^{T}Z}] = \Phi_{X}(\omega)\Phi_{Z}(\omega)$

$= e^{j\omega^{T}\mu_{X}-\frac{1}{2}\omega^{T}P_{XX}\omega}e^{j\omega^{T}\mu_{Z}-\frac{1}{2}\omega^{T}P_{ZZ}\omega}$

$=e^{j\omega^{T}(\mu_{X} + \mu_{Z}) - \frac{1}{2}\omega^{T}(P_{XX} + P_{ZZ})\omega}$

$\therefore Y \sim N(\mu_{X}+\mu_{Z}, P_{XX} + P_{ZZ})$
</center>
<br><br>

## Proof 6.

Prove the fifth feature of a Gaussian random vector.
<br><br>

---

Let $X \sim N(\mu_{X}, P_{XX})$ and $Z \sim N(\mu_{Z}, P_{ZZ})$. Then,

<center>

$p_{X \mid Z}(x \mid z) = \frac{p_{XZ}(x, z)}{p_{Z}(z)} = \frac{p_{Y}(y)}{p_{Z}(z)}$<br><br>
$= \frac{\sqrt{(2\pi)^{p}detP_{ZZ}}e^{-\frac{1}{2}((y-\mu_{Y})^{T}P_{YY}^{-1}(y-\mu_{Y})-(z-\mu_{Z}^{T}P_{ZZ}^{-1}(z-\mu_{Z})))}}{\sqrt{(2\pi)^{n+p}detP_{YY}}}$
</center>

where

+ $P_{YY}^{-1}$ : $\begin{bmatrix}
D^{-1} & -D^{-1}P_{XZ}P_{ZZ}^{-1} \\
-P_{ZZ}^{-1}P_{ZX}D^{-1} & P_{ZZ}^{-1} + P_{ZZ}^{-1}P_{ZX}D^{-1}P_{XZ}P_{ZZ}^{-1}
\end{bmatrix}$

+ $D$ : $P_{XX}-P_{XZ}P_{ZZ}^{-1}P_{ZX}$

To simplify the formula within the curly brackets,

<center>

$(y-\mu_{Y})^{T}P_{YY}^{-1}(y-\mu_{Y})-(z-\mu_{Z})^{T}P_{ZZ}^{-1}(z-\mu_{Z})$

$= (x-\mu_{X})^{T}D^{-1}(x-\mu_{X})$

$-(x-\mu_{X})^{T}D^{-1}P_{XZ}P_{ZZ}^{-1}(z-\mu_{Z})$

$-(z-\mu_{Z})^{T}P_{ZZ}^{-1}P_{ZX}D^{-1}(x-\mu_{X})$

$+(z-\mu_{Z})^{T}(P_{ZZ}^{-1}+P_{ZZ}^{-1}P_{ZX}D^{-1}P_{XZ}P_{ZZ}^{-1})(z-\mu_{Z})$

$-(z-\mu_{Z})^{T}P_{ZZ}^{-1}(z-\mu_{Z})$
<br><br>

$\therefore \ (y-\mu_{Y})^{T}P_{YY}^{-1}(y-\mu_{Y})-(z-\mu_{Z})^{T}P_{ZZ}^{-1}(z-\mu_{Z}) = -\frac{1}{2}((x-\mu_{x \mid z})^{T}P_{X\mid Z}^{-1}(x-\mu_{X \mid Z}))$
</center>

Where

+ $R_{X \mid Z} = D$
+ $\mu_{X \mid Z} = \mu_{X} p_{XZ}P_{ZZ}^{-1}(z-\mu_{Z})$

Therefore, the [conditional probability](https://csh970605.github.io/posts/Probability_RandomVector/#conditional-probability) density function of the random vector $X$ is Gaussian.