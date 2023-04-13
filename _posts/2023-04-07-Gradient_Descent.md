---
title: Gradient Descent 
date: 2023-04-07 04:59:30 +0530
categories: [Optimization]
tags: [machine_learning, artificial_intelligence, optimization, data_science]     # TAG names should always be lowercase
math: true
image:
  path: /assets/img/Gradient_Descent/GD1.png
  alt: Image of path GD takes over a multivariate function. [Source](https://easyai.tech/en/ai-definition/gradient-descent/)
---


<div class="custom" markdown="1" style="font-family: CMS"> 

<style>
    h1, h2 {
        font-family: CMS;
    }
</style>

## Problem Statement 

Consider a function $f: \mathbb{R}^n \rightarrow \mathbb{R}$, our aim is to find the minimum value of the function. Before we begin we could have generalised a bit more, what about functions whose domain is $\subseteq \mathbb{R}^n$. For the time being let us continue with former problem statement.

Let $f(x) = x^2$ be a one-dimensional function whose domain is real line. One can quickly infer its minimum value is 0 and is attained at $x = 0$. One way to see this follows from a keen inspection of derivative, namely by setting it to 0.

**Theorem 1** (First-Order Necessary Conditions) [^1] <br />
*If $x^∗$ is a local minimizer and $f$ is continuously differentiable in an open neighborhood of $x^∗$ , then $\nabla f(x^∗) = 0$.*

## References

[^1]: [Numerical Optimization by Jorge Nocedal, Stephen J. Wright](https://link.springer.com/book/10.1007/978-0-387-40065-5)

</div>
