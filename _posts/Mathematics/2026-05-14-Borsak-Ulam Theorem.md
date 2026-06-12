---
title: Borsuk-Ulam Theorem
date: 2026-05-15 00:23:33 -0500
categories: [Mathematics, Algebraic Topology]
tags: [geometry, topology, ham sandwich theorem]     # TAG names should always be lowercase
summary: A famous named theorem in mathematics, very simple to write and just a nice theorem.
description: In this blog, I will explain the theorem, do some interesting applications and shed light on the proof without going into technicalities.
math: true
---


<div class="custom" markdown="1" style="font-family: Verdana">

## 1. Theorem

Let $f: S^n \rightarrow \mathbb{R}^n$ be a continous function, then there a exist pair of antipodal points[^1] on $S^n$ s.t $f(x) = f(-x)$.

For $n=1$, you can use the following analogy - Let earth be a circle and $f$ be the temperature at each point. The theorem implies there are 2 places on earth with same temperature that are diameterically opposite. 

Let us prove the 1D variant, which is a trivial excercise in calculus-1. Define $g:S^1 \rightarrow \mathbb{R}$ with  $g(x) = f(x) - f(-x)$, our aim is to show $g$ takes the value 0. On 1D circle, to identify each point on circle we use the canonical translation of $S^1$ to $[0,1]$, with end points identified. Let $x \leq 1/2$ then $-x$ is given by $\frac{1}{2} + x$. Evaluating $g$ at 0 and $\frac{1}{2}$ yields following: $g(0) = f(0) - f(\frac{1}{2})$ and $g(\frac{1}{2}) = f(\frac{1}{2}) - f(0)$. Notice the opposite parity of $g(0)$ and $g(\frac{1}{2})$, by continuity (or fancier "intermediate theorem") $g(x)$ take the value 0 for some $0 \leq x \leq \frac{1}{2}$.

We defer the discussion of the general proof for after the applications.

## 2. Applications

*Corollary 1:* No subset of $\mathbb{R}^n$ is homeomorphic to $S^n$. 

This feels very intuitive, but the claim stands firm for pathological subsets of $R^n$ as well. The proof is trivial: Say there is homeo from that subset, $A \subseteq \mathbb{R}^n$, to $S^n$, call it $f$. But also $A$ has the standard inclusion into $\mathbb{R}^n$, i.e $f$ induces a map from $S^n$ to $\mathbb{R}^n$. But by Borsuk-Ulam theorem, a pair of antipodal maps to same point and thus not injective, but as inclusion is injective, $f$ is not injective. A contradiction.

*Corollary 2:* Let $$\{A_i\}_{i=1}^n$$ be a collection of compact disjoint (pairwise) subsets of $\mathbb{R}^n$. There exist a hyperplane that bisects each of the $A_i$'s simultaneously. From bisect we mean divide into 2 halves of equal measure (volume).

For this, you really don't need the heavy machinary of Borsuk-Ulam theorem. One can prove it using simple intuition as well. Here are a few observations - 

1. Fix $A_1$, For every normal vector to the hyperplane, only 1 hyperplane bisects it.

2. Imagine 2D, axis oriented s.t $A_1$ has the bisecting line (hyperplane in 2D) as the x-axis and the normal vector as the y-axis. Now assume the blatantly wrong conjecture: If you rotate the object the bisecting line remains fixed. (Same as saying when you rotate the normal vector to the hyperplane, the hyperplane just rotates at that point, origin, but doesn't wiggle up or down). Assuming this, when you rotate the normal vector, the line sweeps the entirity of plane. I.e. hits $A_2$ at some point. There is an interval when it touches and leaves. Stop when it hits 50% volume, and we are done. But ofcourse the conjecture is wrong (for example consider a wide base object, bisect line lower, and after rotating $180^\circ$ the line by symmetry will go up). However the wiggle will be continous. It will rotate like before and then move up or down to its correct place. With some thought one can convince nothing really has changed, it still sweeps the plane and the exact same logic works.

3. For 3D and higher. You start with bisecting hyperplane for $A_1$. Pick a degree of freedom for the normal vector, rotate it till you bisect $A_2$. Then rotate the normal vector in the other deg of freedom and bisect the third one and so on.

The proof of continuity is a technical detail and as such omitted. It is a fairly believable claim (rotating the object by a small amount produces a small wiggle, upward or downward movement of x-axis i.e.). 

A more formal proof is as follows: A hyperplane is just $\sum_1^n a_i x_i + a_0$, and assume the normal vector is unit length. One can then see this set of hyperplanes as $S^n$ with each point mapping to its obvious hyperplane. This hyperplane may or may not intersect each object. Define the following measure of bisection, per $A_i$: $B_i =$ Vol($A_i \cap H_+$) - Vol($A_i \cap H_-$). Where $H_+$ is the normal facing halve of $\mathbb{R}^n$ as divided by the hyperplane and $H_-$ the other halve. Define $f: S^n \rightarrow \mathbb{R}^n$ as $f(H) = (B_1, B_2, ..., B_n)$. The idea is we want to show $\exists H$ s.t $f(H) = 0$, i.e. $B_i = 0 \ \forall i$. By Borsuk-Ulam theorem, there exist a pair of antipodal points with same image, i.e. $f(x) = f(-x)$. But observe $-x$ is the same hyperplane differently identified (normal is facing the other way). I.e. $f(-x) = -f(x)$. Subbing in the equality we get $f(x) = 0$. Just like before continuity of $f$ is assumed without proof.  

## 3. Proof

I won't do the proof in its generality, it can be found in Hatcher (Algebraic Topology) section 2B.7.

*Claim 1*: Any odd map $f: S^n \rightarrow S^n$, (i.e. $f(x) = -f(-x) \ \forall x$) must have odd degree.

Here degree can be roughly understood as wrapping around. For example, $n=1$, the map $f: S^1 \rightarrow S^1$ given by $z \mapsto z^n$[^2], is to be thought as follows: You have a loop going around $S^1$ in input space. You fix one end, and take the second end and strecth it $n$ times around the circle and then attach back to the first end. The same visual works for higher dimension. Here $n$ will be called the deg of the map. And when $n$ is odd it is an odd degree. That said not all functions need be of this format, one can add wingles in the loop while strecthing and what not. We have a way of defining deg (!) that only honors the overall wrapping. For people familar with homology, say the image of identity generator of $H_n(S^n)$, in input space be, $d e_n$, where $e_n$ is the identity generator of output space homology. Then $d$ is called the degree.

This claim is in some ways intuitive if one thinks about it! Try it on $n=1$.

Assuming this claim, one can get the Borsuk-Ulam theorem. Here is the proof: Let $f: S^n \rightarrow \mathbb{R}^n$ be any cts (continous) function. Consider $g(x) = f(x) - f(-x)$, we have to show $\exists x$ s.t $g(x) = 0$. Notice $g$ is a odd function. Assuming no such $x$ exists, we define $g'(x) = g(x)/\mid g(x) \mid$, another odd function from $S^n \rightarrow S^{n-1}$. Consider the restriction of $g'$ over its equator, i.e. a odd map from $S^{n-1} \rightarrow S^{n-1}$. By previous proposition this is has odd degree. To visualize use $n=2$, a sphere and its equator. The previous claim is saying the loop around equator when moved to output space wraps that circle odd many times. Now the loop around equator in input space is contractible (i.e. null homotopic, or in layman terms we can pull the loop up along upper or lower hemisphere until it shrinks to a point). And extending the process via $g'$ we would wrongly get that the oddly wrapped loop is null homotopic as well, which is incorrect.[^3]

## Footnotes

[^1]: Pair $x$ and $-x$, where $-x$ is diameterically opposite to $x$.

[^2]: We are viewing $S^1 \subseteq \mathbb{C}$.

[^3]: Cleaner mathematical writeup would be: the restriction of $g'$ is null homotopic, and thus the induced maps between homology is 0 and not any odd degree.

</div>
