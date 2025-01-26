---
title: On Random Variables (PENDING)
date: 2024-12-19 15:49:21 +05300
categories: [Mathematics, Probability-Statistics]
tags: [logical, mathematics, probability]     # TAG names should always be lowercase
description: We talk about various convergence notions for random variables
math: true
---

<div class="custom" markdown="1" style="font-family: Verdana">

## 1. Random Variable

It is nothing but a standard "format" to talk about probabilities. Imagine a coin toss or picking 2 numbers out of the hat randomly. Both these are equivalent in terms of probabilistic analysis. And as such we just want placeholder for all of these "similar" experiments. Random Variable thus can be viewed as a box with chits (with number written over it) and we sample from there. The probability of picking a particular number is given by $$P_X(x)$$, where $$X$$ indicate the random variable (or this particular experiment).

Thats one way to look at it, there is another, it is a translation of the "generic" experiment to a particular experiment. Basically a random variable, mathematically speaking, is a function that translate the experiment to a standard one (something like chits out of a box). As such for any probability discussion just on r.v former view suffices, but to make analysis on the case-specific experiment, we inverse translate our experiments and results.

Conceretly speaking, let us first define probability space (our "experiment"). Probability space is a measure-space with total measure equaling 1.

### 1.1 Measure Space

Consider the case of assigning volume (or area / length) to shapes (which is set of points). We are assigning a number to a set, and this mapping is many ways "natural" and thus must follow some natural laws like scaling (double the shape, quadrupled the area or eigth times the volume), translation invariance, decomposibility (area of 2 shapes = sum of area of each indiviual shape). One can informally say that generalization of volume (>3 dimension), i.e. instead of using the "volume" name we call it "measure". Techically, let $$\Sigma$$ be the domain of all points. And $$\mathcal{F}$$ ($$\subseteq 2^\Sigma$$) be the set of all subsets over which measure will be defined. 

>Note: Not all subsets can have a measure and sometimes we just don't care about all the subsets (just a "closed" selection of them). An example for former is Vitali set[^1]. The reason for no possible measure is kind of the definition, we say something is not (lebesgue) measureable (set $$E$$) if when it is used in calculation of any other set's ($$A$$) measure, defined in following way: $$m(A) = m(A \cap E) + m(A \cap E^c)$$, rhs is not equal to lhs. Basically we can always define a generalization of volume[^2] (like how we define area as number of unit squares we can fill), however we also want that when we use that shape in conjunction with some other shape to find volume of the later (as defined above, m being the generalization of unit square filling), it should work and cause no weird discrepancies. And it so happens that there are such weird subsets for which there exist atleast one such $$A$$ for which above doesn't hold. 
{: .prompt-info}

$$\mathcal{F}$$ must satisfy a properties - It should be a $$\sigma$$-algebra[^3] over $$\Sigma$$. It translate to intuitive properties like if a set $$A$$ lies in $$\mathcal{F}$$, which means it is measureable, we also know its complements is not just measureable but also, from properties of measure function, its measure is total measure - measure of set $$A$$, so it should belong in $$\mathcal{F}$$ (in sense why not? $$\mathcal{F}$$ should hold all sets that are measureable in the current setting). And some properties like closed under countable union and intersections. Concretely, $$\Sigma$$ is a $$\sigma$$-algebra over a set $$X$$ is -

1. $$X$$ should $$\in \Sigma$$
2. $$\Sigma$$ is closed under complementation. I.e. if $$A \in \Sigma$$ $$\implies$$ $$A^c \in \Sigma$$.
3. $$\Sigma$$ is closed under countable union. I.e. if $$A_i \in \Sigma \ \forall i \in \mathbb{N}$$ $$\implies$$ $$\cup A_i \in \Sigma$$.

Using de-morgans law we can quickly infer that a $$\sigma$$-algebra is also closed under countable intersection. Also $$\phi$$ (empty set) belongs to the $$\sigma$$-algebra.

Finally, $$\mu$$ be the measure[^4] on domain $$\Sigma$$ and $$\sigma$$-algebra $$\mathcal{F}$$. A measure is just a mapping from the sets ($$\mathcal{F}$$) to extended real numbers. But it too must follow some properties (forsighted in discussionof $$\sigma$$-algebra) -

1. Measure is always non-negative. I.e. $$\forall E \in \mathcal{F}$$, $$\mu(E) \geq 0$$.
2. If $${E_i}$$ are countable collections of sets from $$\mathcal{F}$$ and are pairwise disjoint, then $$\mu(\cup E_i) = \sum \mu(E_i)$$

Here if one of the sets has a finite measure, then $$\mu(\phi)$$ would be 0 (think). A probability space is thus a measure space with the added fact that the total measure $$\mu(\Sigma) = 1$$. You should interpret $$\Sigma$$ as domain of possible outcomes (like 36 outcomes in rolling a dice twice), $$\mathcal{F}$$ as the possible events (subset of $$\Sigma$$ like the set {(1,1), (2,2), ..., (6,6)}, whose english translation could be same number on both dice) and finally $$\mu$$ as the probalility associated to each member of $$\mathcal{F}$$ (here 1/6).

Just like how closure of a set A is the smallest closed set that contains A (one can always take union of 2 closed sets to form a larger closed sets), similarly the smallest $$\sigma$$-algebra for a set A is called its Borel $$\sigma$$-algebra. Basically every set in this algebra is either an element of A or formed by operations of countable union, intersection and complementation. One must note that if measure is defined over some $$\sigma$$-algebra ($$\mathcal{F}$$) for some domain ($$\Sigma$$), then the measure is also defined for the Borel $$\sigma$$-algebra for $$\Sigma$$ (why?).

Long story short, a measure space has 3 components - $$\Sigma$$ (domain of all points), $$\mathcal{F}$$ (subset of superset of $$\Sigma$$) and $$\mu$$ (measure function). They corresponds to specifing set of points (like $$R^2$$), subsets of the space over which measure will be defined, and finally the function that maps those subsets to some non-negative real value (~area). To follow some standard operations, the collection of subsets is deemed to be valid only if it is a $$\sigma$$-algebra.

## References

[^1]: [Wikipedia - Vitali Set](https://en.wikipedia.org/wiki/Vitali_set)
[^2]: [Wikipedia - Lebesgue Measure](https://en.wikipedia.org/wiki/Lebesgue_measure)
[^3]: [Wikipedia - $$\sigma$$-Algebra](https://en.wikipedia.org/wiki/%CE%A3-algebra)
[^4]: [Wikipedia - Measure](https://en.wikipedia.org/wiki/Measure_(mathematics))

</div>
