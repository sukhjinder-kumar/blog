---
title: On Generating Functions (PENDING)
date: 2025-02-03 12:16:08 +05300
categories: [Mathematics, Enumerative-Combinatoric]
tags: [pending, mathematics, counting, permutation, combination]     # TAG names should always be lowercase
description: Explanation and Applications of generating functions
math: true
---

<div class="custom" markdown="1" style="font-family: Verdana">

This post is heavily inspired by [MIT notes on generating functions](https://math.mit.edu/~goemans/18310S15/generating-function-notes.pdf).

## 1. Introduction

Before proceeding with fomal definition, let us have a quick view of the landscape. Let $$a_0$$, $$a_1$$, $$\dots$$ be a sequence of numbers. Define a function, $$f(x)$$ as $$\sum_i a_i x^i$$, where $$i$$ ranges from 0 to $$\infty$$. This is called the generating function for that sequence. In way this is just another way of writing it, $$x$$ being a placeholder. There is one difference though, function can be written more compactly. For example, consider the sequence $$a_i = \binom{N}{i}$$ $$\forall i \leq N$$ and 0 otherwise. The generating function is given by $$f(x) = \sum_{i=0}^{N} \binom{N}{i}x^i$$, notice that $$a_i$$ = 0 $$\forall i \gt N$$ and the function definition is truncated thereof. This can written more compactly as $$(1+x)^N$$[^1]. We can always expand our function and retrieve our sequence. This hints at something more, in retrospect, it might suggest that working with generating functions instead of sequences themselves when interaction amongst multiple sequences is taking place might be rather easier to do, for function manipulation is much easier than handling infinite numbers[^6]. 

Also, say you want to find not the indiviual sequence (for which generating function can still by helpful!) but relations amongst them. For example what is the value of: $$\sum_i a_i$$ or $$\sum_i a_{2i}$$ (or sum of every 5th $$a$$) and what not. Functions when written in compact form can help in such cases (i.e. when not the indiviual values but properties of them as a collection are needed). For the former just find the value of $$F(1)$$ that will give you sum of sequences. I.e. in above $$F(1) = 2^N$$, which is what we expect. For sum of every alternate $$a$$, add $$F(1)$$ and $$F(-1)$$ followed by division by 2, here odd powers gets cancelled out. What about $$\sum_i a_{2i + 1}$$, consider the function $$xF(x)$$, add the value of it at $$x = 1$$ and $$x = -1$$ and divide by 2. Okay clever, what about every 4th power (or arbitary $$\sum_i a_{ki}$$)? Its simple too but requires a bit of trickery. Let $$\omega^0, \omega^1, \omega^2, \text{ and } \omega^3$$ represents 4 roots of unity (i.e. roots of $$x^4 = 1$$). If you add $$F(\omega^0) + F(\omega^1) + F(\omega^2) + F(\omega^3)$$ and divide by 4, you will get the desired sum. For general $$k$$, compute the value of the function at the $$k$$ roots of unity, add them and then divide by $$k$$.[^7] One can be crafty at evaluation and manipulation of the generating function to get desired relations amongst the sequences.

## 2. Formal Definition

Let $$\mathcal{A}$$ be a set and $$S: \mathcal{A} \to \mathbb{R}$$ be a function that assigns "size" to each elements of the set $$\mathcal{A}$$. For example: Let the set $$\mathcal{A}$$ be the set of all binary sequences (0's and 1's) and $$S$$ be the function that maps each sequence to its length (number of digits). Let $$a_n$$ reprsents the number of elements in $$\mathcal{A}$$ of size $$n$$. In our example that would be $$a_0 = 0$$, $$a_1 = 2$$, $$a_2 = 2^2$$, in general $$a_n = 2^n$$. The Generating function is defined accordingly and hereby referenced as $$A(x)$$. For simplicity, whenever we want to say "Let $$\mathcal{A}$$ be a set that has a associated size function", we will assume it suffice to say "Let $$\mathcal{A}$$ be a class of enumerable objects" (i.e. we drop reference to function $$S$$).

## 3. Union of Classes of Enumerable Objects

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

## 4. Product of Classes of Enumerable Objects

Let us now, first motivate and then accordingly define, the product of 2 classes of enumerable objects, i.e $$\mathcal{C} = \mathcal{A} \times \mathcal{B}$$. Consider 2 die of 4 and 6 sides each. We roll them together and note the sum of faces of each die. What is the number of possible configuration of getting the sum $$n$$? One can quickly see that to get a total sum of $$n$$, broadly we can classify the configuration as - 1 coming from first die and $$n-1$$ coming from second, plus 2 coming from first die and $$n-2$$ coming from die, and so on. Another way to represents the same thing is using the generating functions! For the first die, let the class of enumerable objects comprise of all the faces (the size being there face value), $$A(x) = (0x^0 + x + x^2 + x^3 + x^4)$$ and similary for second die $$B(x) = (0x^0 + x + x^2 + x^3 + x^4 + x^5 + x^6)$$. When you multiply these functions, the coefficient of $$x^n$$ represents $$c_n$$ for the very simple reason that each indiviual sum in expansion, of power $$x^n$$, correponds to our picking of 1 size from first class and $$n-1$$ from second and so on. Basically instead of doing the sum ($$c_n = \sum_{i=0}^n a_i b_{n-i}$$) which is tedious and then writing generating function, we are "naturally" able to write generating function without any calculations[^3]. Basically the point being made is - Generating functions are a better and more natural way of working with sequences.

Let us now formalize the result - We define $$\mathcal{C} = \mathcal{A} \times \mathcal{B} = \{(a,b) \mid a \in \mathcal{A} \text{ and } b \in \mathcal{B}\}$$ and the size of $$(a,b) \in \mathcal{C}$$ is $$S_\mathcal{A}(a) + S_\mathcal{B}(b)$$. This "product" definition is quite useful and often good for modelling problems. For example in the above problem, elements in $$\mathcal{C}$$ are of form $$(a,b)$$, where $$a \in \{1, 2, 3, 4\}$$ and $$b \in \{1, 2, 3, 4, 5, 6\}$$, the size is but sum of them. Here $$c_n = \sum_i a_i b_{n-i}$$ and $$C(x) = A(x) \times B(x)$$. The sequence $$c_n$$ is self-explanatory and the generating function requires a small proof, which thus follows.

$$
\begin{align*}
    C^\prime(x) &= A(x) \times B(x) \\
                &= \sum_n a_n x^n \sum_n b_n x^n \\
                &= \sum_i \left(\sum_{j=0}^i a_j b_{i-j}\right) x^i \\
                &= C(x)
\end{align*}
$$

At step 3, to get power $$i$$, one has to multiply powers from both functions s.t they add up to $$i$$. Let us consider the special case when $$\mathcal{A} = \mathcal{B}$$, then $$C(x) = A(x) \times B(x)$$ is $$A(x)^2$$. We can in similar vien define $$\mathcal{A_k} = \mathcal{A_1} \times \dots \mathcal{A_{k-1}}$$, where elements are of form $$(a_1, \dots, a_{k-1})$$ and size is sum of indiviual sizes. One can by induction[^4] or otherwise[^5] show that $$A_k(x) = A_1(x) \times \dots A_{k-1}(x)$$. This is where to able to write generating functions shine! If one were to calculate the sequences first, and then write the function it would be ages. But the generating functions gives a quicker, intutive / natural way to express them without any computation. Here too if all $$\mathcal{A_i}$$ are equal ($$i \in {1, \dots, k-1}$$), then $$A_k(x) = A(x)^k$$. As a quick demonstration, consider $$\mathcal{A}$$ to comprise of "H" and "T", and the size being 1 for "H" and 0 for "T". This models outcome of one coin toss, $$a_n$$ representing number of heads. Here $$\mathcal{A}_k$$ defined as $$\prod_{i=0}^k \mathcal{A}$$ models outcomes after $$k$$ trials (note that $$a_n$$ now defined via sum of co-ordinates still in-sync with our logic of number of heads, one of the illustrations for our point that product is quite handy modelling tool). We can quickly write the generating function as $$A_k(x) = A(x)^k = (1 + x)^k$$.

## 5. Example 1: Modelling via Product of Classes of Enumerable Objects

Consider the problem of ...


## References

1. [MIT notes on generating functions](https://math.mit.edu/~goemans/18310S15/generating-function-notes.pdf).

## Notes

[^1]: This is the binomial theorem, which asserts that $$(1+x)^N$$ is equal to the forementioned sum. The proof follows readily from a few observation. One first must note that (using induction from axioms of the field or otherwise) that $$\prod_{i=1}^{N} (a_{i1} + a_{i2}) = $$ $$\sum_{j_1, j_2, \dots, j_N} a_{1j_1} a_{2j_2} \dots a_{Nj_N}$$, where $$j_k$$ is either 1 or 2. Basically we mean on expansion, without any addition of like terms, each indiviual term is nothing but a combination of terms picked from each of the $$i$$ (ranging from 0 to infinity) "brackets" and multiplied. The total number of pairs $$(j_1, j_2, \dots, j_N)$$ are $$2^N$$, as each $$j_i$$ can take 2 values. Now consider the special case when $$a_{i1} = a$$ and $$a_{i2} = b$$ for every $$i$$, in this case $$\prod_{i=1}^N (a_{i1} + a_{i2})$$ is nothing but $$(a + b)^N$$. But we already know the expansion in sum format, and we notice that there is a lot of repeation of terms, for say $$j_1$$ = 1 and 2 otherwise generates the same term if $$j_2$$ was equal to 1 and all other 2. As a fact we get the equivalent (multiplication is commutative) term $$abbb \dots b$$ ($$b$$ appearing $$N-1$$ times) only when exactly one $$j$$ is 1 and all other 2. The number of such pairs are trivially $$N$$. Similarly we get 2 $$a$$'s and $$N-2$$ $$b$$'s in the sum iff exactly 2 $$j$$'s are 1 and rest all 2, the number of such pairs are $$\binom{N}{2}$$ from elementary combinatoric theory[^proof]. This gives us a shorter sum: $$\sum_{k=0}^N \binom{N}{k} a^k b^{N-k}$$. Replacing $$a$$ with $$x$$ and $$b$$ with 1 gives our desired result.

[^proof]: A quick proof: Consider an array of $$N$$ distinct objects. Number of ways to order them is $$N!$$. Let number of ways to select $$k$$ distinct objects from array of $$N$$ distinct objects be $$C(N, k)$$. In every permutation of the objects read the first $$k$$ elements. But there is a lot of repeatition! As there are $$(N-k)!$$ ordering for which first $$k$$ elements are same. Also we don't care about ordering amongst the elements, i.e. for every set of $$k$$ element (that will appear as first $$k$$ elements in any order) we have $$k!$$ orderings. In short for every unique set of $$k$$ elements we have $$k! \times (N-k)!$$ orderings (out of possible $$N!$$). These are all different amongst themselves (by definition the ordering is different), they are also distinct with orderings for all other $$k$$'s (because the first $$k$$ are elements are different). And the summation of all these strings has to add upto $$N!$$ as it encompasses everything. This will give us $$C(N, k) = \frac{N!}{k! (N-k)!}$$

[^2]: $$c_n$$ represents number of objects of size $$n$$. We know the set, $$\mathcal{C}$$, comprises of elements of $$\mathcal{A}$$ and $$\mathcal{B}$$, and each brings $$a_n$$ and $$b_n$$ elements of size $$n$$, hence the equivalence $$c_n = a_n + b_n$$.

[^3]: Ofcourse if you want generating function in the format of sum of power's of $$x$$, you will have to do the calculations. But you need not always require that. Maybe we can always work in generating function "domain" and once in the end translate the result back to sequences. Plus even it costs the same, it is more easier to write, as many examples to follow will attest.

[^4]: One can write $$\mathcal{A_k} = \mathcal{A^\prime_{k-2}} \times \mathcal{A_{k-1}}$$ where $$\mathcal{A^\prime_{k-2}}$$ is the product of $$\mathcal{A_i}$$'s, $$i \in \{1, \dots, k-2\}$$, (with some exploit of notation) and use result from $$k=2$$ case and induction base step of $$k-2$$.

[^5]: Otherwise would be to follow same pedagogy of arguing that co-efficient of $$i$$th power of $$x$$ would come from taking appropriate power from all functions, and then finally saying that is nothing but $$c_n$$. It's the same thing packed in different facet.

[^6]: Concretely product of classes of enumerable objects. Section 4.

[^7]: What happens here is just like odd powers in case of 1 and -1, that cancel out or there sum (1 + -1) is 0. Here to if we add powers of $$x$$ that aren't multiple of $$k$$, the powers of $$\omega$$ will sum to 0. Only for multiple of $$k$$ they are all 1 and add upto $$k$$, and hence the division at the end. To prove our claim, it suffices to show then: for each power of $$x^{n}$$, $$n$$ not divisible by $$k$$, the powers $$\omega$$ add up to 0 (i.e. $$\sum_{i=0}^{k-1} \omega^{in} = 0$$). It also suffices to show the values $$\omega^{0n}, \omega^{1n}, \omega^{2n}, \dots, \omega^{(k-1)n}$$ maps bijectively (value preserving mapping!) to the set $$\omega^0, \omega^1, \dots, \omega^{k-1}$$, for the sum of later is known to be 0 (as sum of roots is -b/a for a polynomial equation, and for $$x^k = 1$$, b = 0). In cleaner terms this is equivalent to showing the set $$\{0, n, 2n, \dots, (k-1)n\}$$ modulo $$k$$ is a permutation of the set $${0, 1, \dots, k-1}$$. Note that $$\omega^{x} = \omega^{x \text{ mod } k}$$ (if $$\omega$$ is $$k$$th root of unity), i.e. powers of $$\omega$$ are cyclic (or closed under exponentiation w.r.t to the set $$\{\omega^0, \omega^1, \dots, \omega^{k-1}\}$$), this is why our permutation logic holds, for if modulo $$k$$ value is same the power of $$\omega$$ also will be the same. The permutation is mathematically very straightforward, although actually thinking how does that permutation works (which elements maps to which) may be is non-intutive. First, We know that the mapping is onto as modulo $$k$$ limits the maximum value at $$k-1$$ and minimum at 0, and the value is always an integer in-between. Also it is one-one, which can be easily seen by constructing contradiction. Let $$j_1, j_2$$ be 2 distinct multiples of $$n$$ that have same modulo $$k$$. Then $$j_1 - j_2$$ has to be a multiple of $$k$$ (add $$j_1n - j_2n = (km_1 + r) - (km_2 + r)$$, and as $$k$$ doesn't divide $$n$$ we have $$\mid j_1 - j_2 \mid = km_3$$, and $$m_3 \neq 0$$). However maximum difference between $$j_1$$ and $$j_2$$ can be $$k-1$$, hence the contradiction. Before ending this note, one tip: to able to evaluate the functions might also require main, identity like (polynomical factorization) $$x^k - 1 = \prod_{i=0}^k (x - \omega^i)$$ might come handy.

</div>
