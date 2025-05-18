---
title: The Legend of Six
date: 2024-02-08 20:53:20 +0530
categories: [Mathematics, Number-Theory]
tags: [mathematics, number_theory, imo, puzzle]     # TAG names should always be lowercase
description: This post is about the famous problem six in IMO 1988.
math: true
---

<div class="custom" markdown="1" style="font-family: Verdana"> 

## 1. Problem Statment

Consider the following problem: Let $$a$$ and $$b$$ be positive integers such that $$ab + 1$$ divides $$a^2 + b^2$$. Show that below 

$$
\frac{a^2 + b^2}{1 + ab} 
$$

is the square of an integer.

This was the sixth problem in IMO, 1988 head at Canberra. You can find some lores around this in the references

## 2. Approach

We are going to start with our intial value $$(a,b)$$, let the value upon division be $$c$$, and show that some other pair $$(a^\prime, b^\prime)$$ gives the same value upon division. We will follow the same reasoning on $$(a^\prime, b^\prime)$$ and show that this eventually boils down to form $$(a^{\prime \prime}, 0) $$ or $$(0, b^{\prime \prime})$$, from which we would infer $$c$$ is a square of the integer (namely $$a^{\prime \prime}$$ or $$b^{\prime \prime}$$).

## 3. Solution

Let $$(a,b)$$ be the given point, and let the value upon division be $$c$$. On shuffling the equation to resemble a quadratic in variable $$a$$, we note down the other solution via sum of roots equality. To wit $$a + a^\prime = -(-cb)$$ $$= cb$$. This clearly implies the other solution is an integer! And equals $$cb - a$$. Now we will show this second solution, under the condition $$a \geq b \gt 0$$, is $$\lt a, b$$ and $$\geq 0$$. Before showing the proof of this, let us assume it to be true. By symmetry same goes for $$b$$, for which the second solution (by switch of variables) is $$ca - b$$ and under condition $$b \geq a \gt 0$$, is $$\lt a, b$$ and $$\geq 0$$.

Now starting from $$(a,b)$$, assume WLOG $$a \geq b \gt 0$$, we move to $$(cb - a, b)$$. In the 2D grid of solutions we have strictly moved closer to our sought after point (the x/y-axis)! As the x-axis point is strictly less than $$a$$ and non-negative. We repeat our process, we first check which one is the larger[^1], and make the reduction. Now we claim after several of these iterative steps you will get to pair $$(\cdots, 0)$$ or $$(0, \cdots)$$. We can easily show this by contradiction. Suppose the sequence never hit 0 (i.e. niether of $$a$$ or $$b$$ ever equal 0). Now it is easy to see via induction, that if you never get 0, all the points have to be positive (because the next pair is $$\geq$$ 0, but the assumption clearly stipulates no elements is equal to 0). This is clearly false, as the pairs are strictly decreasing[^2], after some steps they will becomes nagative. Hence there exist a pair whose entries are 0. They both can't be as 0's as in one iterate only 1 axis change.

To wrap up the problem let us prove our 2 claims. First let us show the lower bound. As the new root is a solution, putting in the main equation should result in same $$c$$. Now $$c$$ is positive. If the new root is negative the division would be negative[^3]. Second let us see the upper bound. This follows from straight forward computation. The new root, $$cb - a$$, is equal to $$(a^2b + b^3 - a - a^2 b) / (1 + ab)$$, which is nothing but $$(b^3 -a)/(1 + ab)$$. Letting it $$< a$$ and rearraging we get $$ b^3 - ba^2 < 2a$$, which is trivially true as LHS $$\leq 0$$ on grounds of $$a \geq b$$. Similarly we can show it is less than $$b$$.

## 4. Number of Steps

Can we make any upper bound judgements on the number of descent steps? The most simple is the linear upper bound. Say $$a \geq b$$, we know the new root is less than both $$a$$ and $$b$$. I.e. atleast decreases by 1. So after $$a$$ steps of correction in $$a$$ it will surely be $$\leq 0$$. Similarly after $$b$$ steps of correction in $$b$$ it will surely be $$\leq 0$$. So for sure number of descent steps is $$ \leq (a + b)$$ steps.

Can we do better? There is a case when we do a lot better. Say $$a \geq 2b$$, i.e. even further seprated. It is easy to show that the new root is less than $$b/2$$.The calculation is as follows - 

$$
\begin{align*}
    cb - a &= \frac{a^2 + b^2}{1 + ab}b - a \\
           &\lt \frac{a^2 + b^2}{ab}b - a \\
           &= \frac{b^2}{a} \\
           &\leq \frac{b}{2} \\
\end{align*}
$$

Here the last steps follows from our assumption that $$a \geq 2b$$. What it shows is our new $$a$$ shrunk by half compared to previous minimum. Basically consider the min($$a,b$$), it shrank by half (earlier it was $$b$$, now it is $$\lt b/2$$). Notice the new point follows the same inequality but reversed $$b \geq 2a^\prime$$. Hence the min just keeps decreasing by halves. So overall the number of steps this minimum goes to 0 is given by $$\mathcal{O}[\log_2(\min(a,b))]$$.

## 5. References

1. [IMO 1988 Question 6](https://www.imo-official.org/year_info.aspx?year=1988)
2. [Some lores about it](https://www.youtube.com/watch?v=Y30VF3cSIYQ)
3. Solution on [Numberphile](https://www.youtube.com/watch?v=NcaYEaVTA4g&pp=ygUUTGVnZW5kIG9mIHF1ZXN0aW9uIDY%3D)

## 6. Notes

[^1]: If x-coordinate just got the reduction, by our proposition that the new root is less than both $$a, b$$, it will definitely be y-coordinates turn.

[^2]: To define decreasing, we say $$(a^\prime, b^\prime)$$ is less than or equal to $$(a,b)$$ iff $$a^\prime \leq a$$ and $$b^\prime \leq b$$. Strictly less than iff the equality doesn't hold for both.

[^3]: This is because if $$a < 0$$ or $$a \leq -1$$ then $$1 + ab < 0$$. The term is positive only if $$ab > -1$$ or $$b < 1/\vert a \vert < 1$$, which is not possible by the assumption that $$b > 0$$ or $$\geq 1$$.

</div>
