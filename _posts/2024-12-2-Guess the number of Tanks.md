---
title: What is the number of tanks?
date: 2024-12-2 16:35:21 +05300
categories: [Mathematics, Probability-Statistics]
tags: [logical, mathematics, probabilty, statistics]     # TAG names should always be lowercase
description: A simple way to find size of uniform distribution given its samples.
math: true
---

<div class="custom" markdown="1" style="font-family: Verdana">

## 1. Situation

This article is completely insipred, and to a large extent the same content as [this](https://www.youtube.com/watch?v=WLCwMRJBhuI&pp=ygUbbnVtYmVycGhpbGUgbnVtYmVyIG9mIHRhbmtz) numberphile video. The problem goes as follows, there are some number of tanks made, and our task is to guess how many. Each tank is labelled by a serial number. Every once in a while we come across a abandoned tank and note down its serial number. Using this information can we estimate the number of tanks?

## 2. Solution

Say the total number of tanks be $$N$$. Each observation can be thought as a sample from uniform distribution, $$U(0, N)$$. Ignore the fact that earlier serial number are more likely to be found (age, longevity), its a war time! Let the Kth sample be $$a_k$$. Probabilistically, we would like to find value of $$N$$ for which either this is maximum $$P(N \mid a_1, a_2, \dots a_k)$$, or $$P(a_1, a_2, \dots a_k \mid N)$$. 

The former means, what is the best $$N$$ indicated by the observations. Each $$N$$ is given some probability and we choose the best one. This though implies $$N$$ is not fixed but rather probabilitistic. Its like the following example - imagine you start tossing a coin and record number of heads and tails. Upon observation you are asked to find probability of heads. If the coin was a fair one, you would have said 0.5, but for the question let us assume it is not. Whatever the bias be, it still is a number. When one assign probability, one also concede the chance that a less likely $$N$$ or bias can be the solution. In a sense there are no solutions but rather probabilities. This way of thinking is called bayesian statistics. In the later, we are trying to find the N for which the observations are most likely. One assumes that the there no probabilities but rather a single number for our $$N$$, and find the best one. This is called classical inference. To drive home what we mean, let us try to solve these two - 

The later is nothing but $$\frac{1}{N} \times \frac{1}{N-1} \dots \times \frac{1}{N-(K-1)}$$ (replacement not allowed). It is maximized when $$N$$ is as small as possible, and thus equals $$\max(a_1, a_2, \dots a_k)$$. Here while calculating, we assume that $$N$$ is just a regular old fixed number. 

For the former, first let us look at a similar example. Imagine a small basket containing white and black balls. We know there are 2 balls and some good soul told us it is either Black-Black or White-Black. This is equivalent to our $$N$$, it is one of them but don't know which. Upon observation we would like to ascertain which one it is. Classical approach would be, pick a sample and find which setup yields highest likelyhood. So If we get black sample, $$P(B \mid BB) = 1$$ and $$P(B \mid WB) = 1/2$$, by classical inference setup was BB. Or if sample was white, setup was WB. In bayesian approach, we assume some intial knowledge of setup (prior). Say both are equally likely. I.e. P(BB) = P(WB) = 1/2, this is quite interesting, we are thinking of them as not fixed but random. Now say observation was a black ball. 

$$
\begin{align*}
P(BB \mid B) &= \frac{P(BB \text{ and } B)}{P(B)} \\
            &= \frac{P(B \mid BB) P(BB)}{P(BB)P(B \mid BB) + P(WB)P(B \mid WB)} \\
            &= \frac{1 \times 1/2}{1/2 + 1/2 \times 1/2} \\
            &= 2/3
\end{align*}
$$ 

Similarly using bayes rule we get $$P(WB \mid B) = 1/3$$. For our tanks, we assume a similar prior distribution exists for $$N$$, maybe uniform or something alike and modify our beliefs accordingly. Although this is interesting, we in this post explore the classical inference.

Now although mathematically, max, is what we arrive at, it feels a bit loose. Let us first try heuristics, we try to make this estimate better by introducing a "buffer". Suppose the smallest number is $$a_i$$. Now Probabilistically on average, the smallest number is same distance from 1 as the largest number is from $$N$$. We can further say that the average gap between samples is the buffer we should keep between $$N$$ and the largest sample. Following the later, which looks more robust, our prediction would be max + avg. Now avg is nothing but sum of gaps over $$k$$, $$k$$ being number of samples, which is equal to (max - $$k$$) / $$k$$, as the sum of gaps + number of number is equal to max. So our predictor is max + (max - $$k$$) / $$k$$.


Now both max, and max + avg are predictors, each with its own logical backing. There can be many more, like find the average of all samples and multiply by 2 (idea being taking average will be near midpoint and double will give $$N$$). How to do we say when a predictor is better or worse? There are several criterions like - 

1. The simplest, as $$k$$ approach a larger number our estimate should converge to $$N$$.
2. It should be unbiased estimator. What does it mean? Good question. It basically says if you repeat your experiment many times, and from experiment we mean observing k samples, like imagine bunch of people trying to predict the $$N$$ based on there own set of $$K$$ observations, the average prediction should be $$N$$. It is different from 1. $$k$$ is fixed, just that on average we expect to be close to $$N$$, where average is taken over $$k$$ observations.
3. The distribution of our estimate should be concentrated near the mean, i.e. small variance. This basically corresponds to saying, yes on average you get $$N$$ (point 2), but also on a particular case you aren't far off from $$N$$.

The first is a bit nuanced and we defer it to some another post. For now let us deal with other 2 first for each of the 3 predictors. We will shift to uniform distribution over reals instead of discrete points, as it massively simplifies our calculation. This ofcourse doesn't mean at all that results translate to discrete case. Just that the idea still holds and one can do the calculations in similar vein. For the max + avg, note that the number "length" is non-existent, so it is just max/$$k$$. 

Starting with just max, what is the expectation and variance? To find those we require the probability distribution. Proceding with standard method of first calculating the CDF and then differentiating to find PDF, we get - $$F(max(a_1, \cdots a_k) \leq y)$$ which is nothing but $$\prod_i F(a_i \leq y)$$ or $$(y/N)^k$$. Hence the CDF is given by $$f(y) = k \times y^{k-1} / N^k$$.

$$
\begin{align*}
    E[\hat{\theta}_\max] &= \int_0^N \hat{\theta}_\max \times P_{\hat{\theta}_\max \sim a_i} (\hat{\theta}_\max) d\hat{\theta}_\max \\
    &= \int_0^N \hat{\theta}_\max \times k \times \hat{\theta}_\max^{k-1} / N^k d\hat{\theta}_\max \\
    &= \frac{k}{k+1} N
\end{align*}
$$

Similarly the variance is - 

$$
\begin{align*}
    \text{Var}[\hat{\theta}_\max] &= E[\hat{\theta}_\max^2] - E[\hat{\theta}_\max]^2 \\
    &= \int_0^N \hat{\theta}_\max^2 \times P_{\hat{\theta}_\max \sim a_i} (\hat{\theta}_\max) d\hat{\theta}_\max - \frac{k^2}{(k+1)^2} N^2 \\
    &= \int_0^N \hat{\theta}_\max^2 \times k \times \hat{\theta}_\max^{k-1} / N^k d\hat{\theta}_\max - \frac{k^2}{(k+1)^2} N^2\\
    &= \frac{k}{k+2} N^2 - \frac{k^2}{(k+1)^2} N^2 \\
    &= \frac{k}{(k+1)^2(k+2)}  N^2
\end{align*}
$$

One notices that on avg with max as the predictor, we are always underestimating. It is a biased estimator. Let us define a new predictor which is nothing but $$(k+1)/k \times \max$$. One quickly realizes this is nothing but our max + avg! Clearly its expectation is $$N$$, using the fact that $$E[aX] = aE[X]$$. Also we know $$\text{var}(aX) = a^2 \text{Var}(X)$$, giving var(max + avg) = $$1/(k)(k+2)N^2$$. Hence although max + avg is a unbiased estimator, it has larger variance compared to just max.

Lastly for twice the average estimator ($$\hat{\theta} = 2 \times \frac{\sum_{i=1}^{i=k} a_i}{k}$$), the mean is nothing but N using the property $$E[\sum_i X_i] = \sum_i E[X_i]$$, and each of the samples are i.i.d. Similarly variance, using the fact that $$\text{var}(\sum_i X_i) = \sum_i \text{var}(X_i)$$ if $$X_i$$ are i.i.d, we have var(twice the avg) = $$N^2/3k$$. We note that max + avg has less variance than twice the average for $$k \geq 1$$. As such this is the best amongst our options.

</div>
