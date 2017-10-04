---
layout: post
title: Fourier Analysis and the Mathematics behind it
author: Author Heming
---

Suppose we have a set of n linearly independent elements

$$ c_1 u_1 + c_2 u_2 + ... + c_n u_n = 0 \ \ iff \ \  c_1 = c_2 = ... = c_n = 0. $$

## Best approximation in normed linear spaces

Then {u_n} form a basis for the finite-dimensional linear normed space Sn.

In the case of infinite-dimensional spaces X, S_n is a n-dimensional subspace of X.

Now let v be an random element in X, then the *best approximation* in Sn is given by the element vn \in Sn that is closest to v in terms of the norm defined by the space.

$$ \Delta_n = min || x-v || = || v_n - v || $$

We denote the approximation v_n by

$$ v_n = arg min_{x\in S_n} || x-v || $$

Since the approximation v_n lies in S_n, it will have an expansion in the basis set, i.e.

$$ v_n = c_1 u_1 + c_2 u_2 + ... + c_n u_n $$

The associated approximation error is \Delta_n. When we increase the number of basis vectors u_n, the approximation will get better( at lease cannot get worse, because if basis elements u_k are not used, the associated coefficients are zero). When n -> \infty, the subspace approaches infinite-dimensional space, the approximation will be close to zero. 

## Best approximation in Hilbert Space

To discuss about Fourier analysis, we need to introduce Hilbert Space (complete inner product space). As we need to discuss the orthogonality of the basis. An orthogonal set in Hilbert Space is

$$ <u_i, u_j> = 0 \  for \  i \neq j. $$

Theorem: Let {e1, e2, ..., en} be an orthonormal set in a Hilbert space H. Define Y = span{e_i}^n_{i=1}, to be subspace of H. Then for any x \in H, the best approximation of x in Y is given by unique element

$$ y = \sum_{k=1}^n c_k e_k $$


$$ c_k = <x, e_k> $$

c_k are the Fourier coefficients of x with respect to the set.

Proof: The theorem can be proved by fining the minimal of the norm of the approximation (take the derivative).


This is the math behind Fourier Decomposition. In essence, we are using a finite-dimensional inner product space to approximate an element in Hilbert space. To express that, we use a set of orthonormal basis, and the coefficients are the inner product between the element and corresponding basis.  

<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>


