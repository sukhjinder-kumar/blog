---
title: A First Course in Optimization (PENDING)
date: 2023-04-07 04:59:30 +0530
categories: [Mathematics, Optimization]
tags: [machine_learning, artificial_intelligence, optimization, data_science, theory_course]     # TAG names should always be lowercase
summary: Gradient Descent is a very powerful optimization algorithm that is used almost everywhere in machine learning, from solving logistic regression in 1950s to GPT3! This post is math intensive, we try to give a comprehensive analysis.
description: Gradient Descent is a very powerful optimization algorithm that is used almost everywhere in machine learning, from solving logistic regression in 1950s to GPT3!
math: true
image:
  path: /assets/img/Gradient_Descent/GD1.png
  alt: Image of path GD takes over a multivariate function. [Source](https://easyai.tech/en/ai-definition/gradient-descent/)
---

<div class="custom" markdown="1" style="font-family: CMS"> 

You can play with the algorithms [here](https://sukhjinder-kumar-descent-algorithms.streamlit.app/) and checkout the implementation details [here](https://github.com/sukhjinder-kumar/DescentAlgorithms)

## Problem Statement 

Consider a function $f: \mathbb{R}^n \rightarrow \mathbb{R}$, our aim is to find the minimum value of the function. Now before we begin we could have generalised a _little_ bit more, what about functions whose domain is $\subseteq \mathbb{R}^n$. But for the time being let us continue with former problem statement.

Let $f(x) = x^2$ be a one-dimensional function whose domain is real line. One can quickly infer its minimum value is 0 and is attained at $x = 0$. One way to see this follows from a keen inspection of derivative, namely by setting it to 0.

__Theorem 1__ (First-Order Necessary Conditions) [^1] <br />
_If $x^∗$ is a local minimizer and $f$ is continuously differentiable in an open neighborhood of $x^∗$ , then $\nabla f(x^∗) = 0$._

_Proof._ We prove by contradiction. Assume wrongly that gradient is non-zero at $x^\*$. If we now move in direction opposite to gradient we are bound to attain a lower value of function! We are using the fact that gradient points in direction of greatest ascent and consequently opposite direction points to steepest descent. Hence by contradiction, $\nabla f(x^\*) = 0$.



## Further Resources

## References

[^1]: [Numerical Optimization by Jorge Nocedal, Stephen J. Wright](https://link.springer.com/book/10.1007/978-0-387-40065-5)

</div>
