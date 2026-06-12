---
title: Another Prisonder Escape Puzzle
date: 2025-06-29 17:01:12 +05300
categories: [Puzzle]
tags: [mathematics, puzzle]     # TAG names should always be lowercase
description: An interesting puzzle.
math: true
---

<div class="custom" markdown="1" style="font-family: Verdana">

## 1. Problem Statement[^1]

You have got 100 prisoners who are allowed to strategies beforehand. One by one they will enter the room, pick 50 out of 100 boxes, and leave out the room. Once the prisoner has entered the room, they aren't allowed to talk back (think of as keeping them in separate room afterwards). Inside the boxes are the numbers 1 to 100, placed randomly amongst the 100 boxes. Each prisoner is also labelled from 1 to 100. If each prisoner finds their label amongst the 50 boxes, they all will be freed. Navielly, the probability of this happening is $$(1/2)^{100}$$, which is practically 0. Can you improve this (by a lot!)?


## 2. Solution

Before I dwell into the answer, it is morally unfair for me to take the high ground. I heard the problem in a bit more forgiving terms. The same setup but basically with a hint. Consider the following problem - "100 prisoners, 100 boxes (same setup) but now the first guy who goes in has a special power, he can see content of each box and swap the contents of 2 boxes. Does there exist a strategy which allows all to find there label?"

Here is one more hint, think of arrays and cycles in them (very computer science interview puzzle, sort of similar to minimum swaps needed to sort an array). 

For the mentioned problem, notice that there can be atmost 1 cycle of length greater than 50. Where cycle is defined as follows - You pick a box (say 1), it has some label (say 50), you pick the box 50, it contained the label 100, and lastly box 100 contained 1. The cycle then would be $$50 \rightarrow 100 \rightarrow 1$$ of length 3. Consider the strategy where each prisoner first picks the box with his own label (like the first prisoner picks 1st box, and ith prisoner picks ith box), and follows the cycle. If say the boxes are arranged s.t there is no cycle of length greater than 50, each will find there label (as a fact it will be the last element in there cycle, as that will map to ith box they started with by definition). And if no, prisoner 1 can use his power to swap appropriately to ensure no cycle is of length greater than 50[^2]. 

Back to our original problem. Just follow the same strategy, but without the magical power of prisoner 1, you can't always guarantee that there is no cycle of length greater than 50. But it turns out the probability that there is no cycle of length greater than 50 is non-zero and considerable. Namely, 

$$
\begin{align*}
    \text{Probability(Cycle greater than 50)} &= \frac{99! + \binom{100}{1} 98! + \binom{100}{2}2!97! \ldots + \binom{100}{49}49!50!}{100!} \\
    &= 1/100 + 1/99 + \ldots + 1/51 \\
    &= 0.688
\end{align*}
$$

The above calculation follows as - count number of permutation containig a cycle length 100, 99, upto 51. For say cycle length $x$, you have $(x-1)!$ ways to arrange them (fix anyone and permute the rest), $\binom{100}{100-x}$ to select non-cycle element and $(100-x)!$ to permute them however you like. Thus probability that there is no cycle is roughly 0.3, and so is the success probability of our strategy. 

If there are $N$ prisoners[^3] (say $N$ even for simplicity, and call $m = N/2$), the success probability would be $1 - (1/(m + 1) + 1/(m+2) + \ldots + 1/N)$, which by elementary calculus[^4] is $1 - \ln(2)$, roughly 0.3.

Also, I should mention I don't know if this is optimal. This is just a lucky strategy that worked well.

## References

[^1]: [Veritasium: The Riddle That Seems Impossible Even If You Know The Answer](https://www.youtube.com/watch?v=iSNsgj1OCLA)

[^2]: This is easily done as well. You can imagine the cycle as element lying on a circle, just swap the diameterically opposite points. In worst case of cycle length 100, this procedure gives 50 ways to break it into 2 50-cycles.

[^3]: In the general case with $N$ prisoners, each prisoners has $m = N/2$ tries to find there label in the $N$ boxes.

[^4]: The general sum can be written as $\sum_0^{m - 1} 1/(N - i)$, which is same as $\sum 1/(1 - i/N) 1/N$. From the definition of reimann sum we see this is equal to $\int_0^{0.5} 1 / (1-x) dx = ln2$.

</div>
