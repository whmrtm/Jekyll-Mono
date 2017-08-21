---
layout: post
title: Hilbert Transform
author: Author Heming
---
Hilbert Transform is a great tool for analyzing non-stationary time series. Fourier transform is defined as 

$$ f(x) = \frac{1}{2}a_0 + \sum_0^{\infty} a_n cos \frac{nx}{\lambda} + b_n sin \frac{n\pi}{\lambda}$$

The coefficients can be ontained by multiplying both sides of equations with cos(mx/lambda) or sin(mx/lambda) and integrating over a period of interval.


## Rewrite the form
After obtaining the coefficients, the equation can be written as

$$ f(x) = -\frac{1}{2\pi}[\int_{-\pi \lambda}^{\pi \lambda} f(t) dt] \Delta u + \frac{1}{\pi} \sum_{n=0}^{\infty}[\int_{-\pi/\lambda}^{\pi/\lambda} f(t)cos u_n(x-t) dt] \Delta u $$

The summation can be viewed as Riemann sum over the positive real line. Omitting al the details, take the limit to infinity, produce the following result

$$ f(x) = \frac{1}{\pi} \int_0^{\infty} du \int_{-\infty}^{\infty} f(t) cos u(x-t) dt $$

 This is known as *Fourier's integral formula*.

 ## The Hilbert Transform

 Fourier integral formula may be considerd as limit y->0 of the following function of two real variables

 $$ U(x,y) = \int_{0}^{\infty}[a(t)cos xt + b(t) sin xt] e^{-ty} dt $$

 This function is actually the real part of a complex valued function

 $$  \phi(z) = \int_0^{\infty} [a(t) - ib(t)]e^{izt} dt $$

 It can be verified that the real part and the imaginary part satisfy Cauchy-Riemann condition. Also the function is analytic .

lets call the imaginary part as g(x), and

$$ g(x) = \frac{1}{\pi} \int_0^{\infty} du \int_{-\infty}^{\infty}f(t) sin u(x-t)$$

Leave out the calculation details, it can be computed that

$$ g(x) = -\frac{i}{\sqrt(2\pi)} \int_{-\infty}^{\infty}F(u)sgn(u)e^{iux}du $$ 

And the Fourier transform 

$$ G(u) = -iF(u)sgn(u) $$

Finally we can get the *Hilbert transform* of f(t)

$$ g(x) = \frac{1}{\pi} \int_{-\infty}^{\infty} \frac{f(s)}{x-s} ds $$ 

## Usage of the Hilbert transform

The complex form f(x)+ig(x) is the analytic form of the signal f(x). Using the analysic form we can calculate the instantaneous phase and frequency of the signal.

$$ \omega(t) = \frac{d\theta(t)}{dt} $$

<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
