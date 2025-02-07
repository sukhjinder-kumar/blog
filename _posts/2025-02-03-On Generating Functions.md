---
title: On Generating Functions (PENDING)
date: 2025-02-03 12:16:08 +05300
categories: [Mathematics, Enumerative-Combinatoric]
tags: [mathematics, counting, permutation, combination]     # TAG names should always be lowercase
description: We talk about generating functions
math: true
---

<div class="custom" markdown="1" style="font-family: Verdana">

## 1. Introduction

Before proceeding with fomal definition, let us have a quick view of the landscape. Let $$a_0$$, $$a_1$$, $$\dots$$ be a sequence of numbers. Define a function, $$f(x)$$ as $$\sum_i a_i x^i$$, where $$i$$ ranges from 0 to $$\infty$$. This is called the generating function for that sequence. In way this is just another way of writing it, $$x$$ being a placeholder. There is one difference though, function can be written more compactly. For example, consider the sequence $$a_i = \binom{N}{i}$$ $$\forall i \leq N$$ and 0 otherwise. The generating function is given by $$f(x) = \sum_{i=0}^{N} \binom{N}{i}x^i$$, notice that $$a_i$$ = 0 $$\forall i \gt N$$ and the function definition is truncated thereof. This can written more compactly as $$(1+x)^N$$[^1]. We can always expand our function and retrieve our sequence. This hints at something more, in retrospect, it might suggest that working with generating functions instead of sequences themselves when interaction amongst multiple sequences is taking place might be rather easier to do, for function manipulation is much easier than handling infinite numbers.

## 2. Formal Definition

Let $$\mathcal{A}$$ be a set and $$S: \mathcal{A} \to \mathbb{R}$$ be a function that assigns "size" to each elements of the set $$\mathcal{A}$$. For example: Let the set $$\mathcal{A}$$ be the set of all binary sequences (0's and 1's) and $$S$$ be the function that maps each sequence to its length (number of digits). Let $$a_n$$ reprsents the number of elements in $$\mathcal{A}$$ of size $$n$$. In our example that would be $$a_0 = 0$$, $$a_1 = 2$$, $$a_2 = 2^2$$, in general $$a_n = 2^n$$. The Generating function is defined accordingly and hereby referenced as $$A(x)$$. For simplicity, whenever we want to say "Let $$\mathcal{A}$$ be a set that has a associated size function", we will assume it suffice to say "Let $$\mathcal{A}$$ be a class of enumerable objects" (i.e. we drop reference to function $$S$$).

## 3. Union and Cartesian Product of Classes of Enumerable Objects

Let $$\mathcal{A}$$ and $$\mathcal{B}$$ be two disjoint (no element in common) classes of enumerable objects. Let us define a third class of enumerable objects, $$\mathcal{C}$$, whose elements $$\in \mathcal{A} \cup \mathcal{B}$$, and each elements retains there size function. I.e. $$S_\mathcal{C}: \mathcal{A} \cup \mathcal{B} \to \mathbb{R}$$ is nothing but -

$$
\begin{align*}
    S_\mathcal{C}(x) = 
    \begin{cases}
        S_\mathcal{A}(x), & \text{if } x \in \mathcal{A}, \\
        S_\mathcal{B}(x), & \text{if } x \in \mathcal{B}.
    \end{cases}
\end{align*}
$$

We will refer, in shorthand, to this as $$\mathcal{C} = \mathcal{A} \cup \mathcal{B}$$, i.e defined a union operation of class of enumerable objects. In this case $$C(x)$$ takes a very natural form of $$A(x) + B(x)$$, for $$c_n$$ is nothing but $$a_n + b_n$$ (why?[^2]). Nothing interesting happending up until now, but product is where things get interesting.

Let us now, first motivate and then accordingly define, the product of 2 classes of enumerable objects, i.e $$\mathcal{C} = \mathcal{A} \times \mathcal{B}$$.

## Notes

[^1]: This is the binomial theorem, which asserts that $$(1+x)^N$$ is equal to the forementioned sum. The proof follows readily from a few observation. One first must note that (using induction from axioms of the field or otherwise) that $$\prod_{i=1}^{N} (a_{i1} + a_{i2}) = $$ $$\sum_{j_1, j_2, \dots, j_N} a_{1j_1} a_{2j_2} \dots a_{Nj_N}$$, where $$j_k$$ is either 1 or 2. Basically we mean on expansion, without any addition of like terms, each indiviual term is nothing but a combination of terms picked from each of the $$i$$ (ranging from 0 to infinity) "brackets" and multiplied. The total number of pairs $$(j_1, j_2, \dots, j_N)$$ are $$2^N$$, as each $$j_i$$ can take 2 values. Now consider the special case when $$a_{i1} = a$$ and $$a_{i2} = b$$ for every $$i$$, in this case $$\prod_{i=1}^N (a_{i1} + a_{i2})$$ is nothing but $$(a + b)^N$$. But we already know the expansion in sum format, and we notice that there is a lot of repeation of terms, for say $$j_1$$ = 1 and 2 otherwise generates the same term if $$j_2$$ was equal to 1 and all other 2. As a fact we get the equivalent (multiplication is commutative) term $$abbb \dots b$$ ($$b$$ appearing $$N-1$$ times) only when exactly one $$j$$ is 1 and all other 2. The number of such pairs are trivially $$N$$. Similarly we get 2 $$a$$'s and $$N-2$$ $$b$$'s in the sum iff exactly 2 $$j$$'s are 1 and rest all 2, the number of such pairs are $$\binom{N}{2}$$ from elementary combinatoric theory[^proof]. This gives us a shorter sum: $$\sum_{k=0}^N \binom{N}{k} a^k b^{N-k}$$. Replacing $$a$$ with $$x$$ and $$b$$ with 1 gives our desired result.

[^proof]: A quick proof: Consider an array of $$N$$ distinct objects. Number of ways to order them is $$N!$$. Let number of ways to select $$k$$ distinct objects from array of $$N$$ distinct objects be $$C(N, k)$$. In every permutation of the objects read the first $$k$$ elements. But there is a lot of repeatition! As there are $$(N-k)!$$ ordering for which first $$k$$ elements are same. Also we don't care about ordering amongst the elements, i.e. for every set of $$k$$ element (that will appear as first $$k$$ elements in any order) we have $$k!$$ orderings. In short for every unique set of $$k$$ elements we have $$k! \times (N-k)!$$ orderings (out of possible $$N!$$). These are all different amongst themselves (by definition the ordering is different), they are also distinct with orderings for all other $$k$$'s (because the first $$k$$ are elements are different). And the summation of all these strings has to add upto $$N!$$ as it encompasses everything. This will give us $$C(N, k) = \frac{N!}{k! (N-k)!}$$

[^2]: $$c_n$$ represents number of objects of size $$n$$. We know the set, $$\mathcal{C}$$, comprises of elements of $$\mathcal{A}$$ and $$\mathcal{B}$$, and each brings $$a_n$$ and $$b_n$$ elements of size $$n$$, hence the equivalence $$c_n = a_n + b_n$$.

</div>
