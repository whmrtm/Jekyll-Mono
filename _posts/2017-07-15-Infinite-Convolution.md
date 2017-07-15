---
layout: post
title: Infinite Convolution
author: Author Heming
---

## Some Thoughts on Convolution
Encountered this problem when dealing with some iterative process. The question I wondering is 'what is the form of n fold convolution when n goes to infinity?' That is, given a initial filter $\omega$, find the result of infinite self-convolution
$$ \omega^{*n}, n\to\infty$$

The problem can be solved by central limit theorem. According to central limit theorem
 > In probability theory, the central limit theorem (CLT) establishes that, for the most commonly studied scenarios, when independent random variables are added, their sum tends toward a normal distribution (commonly known as a bell curve) even if the original variables themselves are not normally distributed.

The density of sum of two independent random variables can be viewed as the convolution of the density function of the original variables. 

Therefore, by applying that theorem, we can conclude that **no matter** what initial filter we choose, the result will 'converge' to a Gaussian.

Wikipedia provides a good example, and I cite them here

![alt](https://upload.wikimedia.org/wikipedia/commons/a/a6/Central_limit_thm_1.png)

![alt](https://upload.wikimedia.org/wikipedia/commons/f/f8/Central_limit_thm_2.png)

![alt](https://upload.wikimedia.org/wikipedia/commons/6/69/Central_limit_thm_3.png)

![alt](https://upload.wikimedia.org/wikipedia/commons/8/85/Central_limit_thm_4.png)

Source: https://en.wikipedia.org/wiki/Illustration_of_the_central_limit_theorem