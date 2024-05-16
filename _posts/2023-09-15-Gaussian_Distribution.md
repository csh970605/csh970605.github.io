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

Gaussian distribution also known as normal distribution is a type of continuous probability distribution.<br>
The general form of its [probability density function](https://csh970605.github.io/posts/Probability_RandomVector/#probability-density-function) is :

<center>

$f(x) = \frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{1}{2}(\frac{x-\mu}{\sigma})^2}$<br>

</center>

Where <br>

+ $\mu$ : The mean or expectation of distribution.<br>
+ $\sigma$ : standard deviation.


Since gaussian distribution is calculated by two probability information, that is, expectation and distribution, it is easy to treat mathematically. And also, since lots of signals from nature is similiary to gaussian distribution, it is usually used to model the various social, nature phenomenons.

The shape of gaussian distribution is:

<center>

<img src="https://github.com/csh970605/csh970605.github.io/assets/28240052/04a3e688-62ca-45e3-b253-73717f7bb95d">
</center>

<br><br><br><br>


# Gaussian Random Vector

The probability density function of gaussian [random vector](https://csh970605.github.io/posts/Rand_Vector/) $X$ is defined as formula[1].

<center>

$p_{X}(x) = N(x \mid \mu_{X}, P_{XX})$

<p align="center">
    <span>$= \frac{1}{\sqrt{(2 \pi)^{n}detP_{XX}}}e^{-\frac{1}{2}(x-\mu_{X})^{T}P_{XX}^{-1}(x-\mu_{X})}$</span>
    <span style="float: right;">[1]</span>
</p>

</center>

Where

+ $\mu_{X}$ : Expectation.
+ $P_{XX}$ : Covariance.
+ $n$ : Dimension of $X$.
+ $detP_{XX}$ : determinant of $P_{XX}$.

The gaussian random variable $X$ is expressed simply as $X \sim N(x \mid \mu, \sigma^{2})$, and the gaussian random vector X is expressed simply as $X \sim N(X \mid \mu_{X}, P_{XX})$

There are images that drawing the shape of 2-dimensional gaussian probability density function following several expectations and covariances:

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

According to the images above, if the values of off-diagonal terms are 0, the contour is a circle around the expectation, and if the values of off-diagonal terms are not 0, the contour is a ellipse around the expectation. You can see the proof [here](https://csh970605.github.io/posts/Gaussian_Distribution/#proof).

<br><br>

## Joint Gaussian Random Vector

If the random vector $Y = \begin{bmatrix}
X \\
Y
\end{bmatrix}$ that consist of random vector $X$ and $Y$ has gaussian distribution,

<br><br><br><br>


# Characteristic Function of Gaussian Random Vector

The [characteristic function](https://csh970605.github.io/posts/Rand_Vector/#characteristic-function) of random vector $N(x \mid \mu_{X}, P_{XX})$ is:

<center>

$\Phi_{X}(\omega) = e^{j\omega^{T} \mu_{X} - \frac{1}{2} \omega^{T}P_{XX}\omega}$

</center>


<br><br><br><br>


# Proof

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

Where $c_{2}$ is a constant.

Because $P_{XX}$ is a positive-definite matrix, it has eigenvalue $\lambda_{1}, \lambda_{2}$ which are bigger than 0, and eigenvector $v_{1}, v_{2}$ which are orthogonal. Thus, we can divide $P_{XX}$ as:

<center>

$P_{XX} = E\wedge E_{T}$
</center>

Where

+ $E$ : $\begin{bmatrix}
v_{1} & v_{2}
\end{bmatrix}$

+ $\wedge$ : $diag(\lambda_{1}, \lambda_{2})$

+ $E^{T}E$ : $I$


Since $P_{XX}^{-1} = E \wedge^{-1} E^{T}$ accordingly, let $y = E^{T}(X- \mu_{X})$. Then, the formula $(x-\mu_{X})^{T}P_{XX}^{-1}(x-\mu_{X})$ becomes:

<center>

$(x-\mu_{X})^{T}P_{XX}^{-1}(x-\mu_{X}) = (x-\mu_{X})^{T}E \wedge^{-1} E^{T}(X-\mu_{X})$

$= y^{T}\wedge^{-1}y$

$= \frac{y_{1}^{2}}{\lambda_{1}} + \frac{y_{2}^{2}}{\lambda_{2}} $

$= c_{2}$
</center>

where $y=\begin{bmatrix}
y_{1} & y_{2}
\end{bmatrix}^{T}$.

So, the contour of gaussian probability density function is an ellipse centered around $\mu_{X}$, the length of the main axis is $sqrt{\lambda_{1}}$ and $sqrt{\lambda_{2}}$, and the direction of the main axis is $v_{1}, v_{2}$ respectively.

