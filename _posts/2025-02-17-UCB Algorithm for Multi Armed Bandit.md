---
title: UCB Algorithm for Multi Armed Bandit (PENDING)
date: 2025-02-17 20:43:32 +05300
categories: [Computer-Science, Multi-Arm-Bandit]
tags: [pending, mathematics, computer_science, multi_armed_bandit, bandit, algorithm, ucb]     # TAG names should always be lowercase
description: Upper Confidence bound algorithm for multi armed bandit problem. We also derive its regret bounds and show that is sublinear and thus better than naive algorithms.
math: true
image:
  path: /assets/img/MultiArmedBandit/multiarmedbandit.jpg
  alt: Image of an octopus deciding between pulling levers of slot machines.
---

<div class="custom" markdown="1" style="font-family: Verdana">

## 1. Problem Statement

Consider $$K$$ slot machines and each gives some reward when its lever is pulled. You can only select one machine at a time and observe its reward. The reward given by machine is determined by some internal logic like fixed reward, bernoulli reward with some probability (i.e 1 reward with probability $$p$$ and 0 with probability 1-$$p$$), guassian with some mean and variance, or any other distribution for each arm. Our task is to accumulate maximum rewards over some time horizon $$T$$[^1]. The beauty of this problem is, it exploration vs exploitation in its purest form (as we shall soon see).

Consider the offline setting, when you know the internal logic (or reward distribution) of each machine (or arm), which arm should we pull at each time step to have the maximum cummulative reward? Before answering, we first need to a bit careful about defining our objective. As things are random, any strategy on a bad day can falter. Inspired thus we define our objective as: $$\mathbb{E}[\sum_{t=1}^T R_t]$$. In offline setting the best thing to do is - select the arm with largest mean reward. The proof is rather obvious, to put in ink we say - our objective is equal to $$\sum_t \mathbb{E}[R_t]$$, and as we are selecting the arm with maximum $$\mathbb{E}[R]$$, we are piecewise maximizing this sum.

This was rather boring. The real fun lies in the online setting. Now suppose that we don't know the reward distribution, how to maximize our cummulative reward. To highlight the main theme of exploration vs exploitation, and also to get started, we first present the "Naïve Algorithm".

## 2. Naïve Algorithm

This algorithm is simple: Pick each machine, sequentially, $$T/K$$ times[^2]. The machine is doing no exploitation, it goes one by one and learns each machine dynamics (reward history to produce average reward, and other statistical measures). How does it fair? This being so simpleton and the fact that if $$T$$ is too large after some point pulling a particular arm wouldn't make a tangible difference in our statistical parameters and its better to move on. As those extra tries acculumated can be spent on the optimal machine. Let us quantify our algorithm though. In practice we don't try to maximize our reward, rather minimize cummulative regret defined by: $$\mathcal{R}_T = T\mu^* - \mathbb{E}[\sum_t R_t]$$, where $$\mu^*$$ is the best average reward. It encodes how much reward we lost, overall, from the theoretical best. 

Let the arms be denoted by $$i = 1, 2, \dots K$$ and $$\mu_i$$ be there (actual) mean rewards. Further let $$\mu^*$$ be the largest amongst them. The following re-writing of regret is general and we will used later in regret calculation of UCB as well.

$$
\begin{align*}
    \mathcal{R}_T &= T\mu^* - \mathbb{E}\left[\sum_t R_t\right] \\
                  &= \mathbb{E}\left[\sum_t \mu^* - R_t\right]  = \mathbb{E}\left[\sum_t \Delta^\prime_t \right] \\
                  &= \mathbb{E} \left[\sum_t \sum_{i=1}^K \mathbb{1}_{a = i}\Delta^\prime_i \right] \\
                  &= \sum_i \mathbb{E}[T(i)] \Delta_i
\end{align*}
$$

$$\Delta_i$$ represents $$\mu_* - \mu_i$$, and $$T(i)$$ represents the number of times that particular arm ($$i$$) was pulled. All this fancy calculation says is, the total regret is equal to regret added per machine. If you picked first machine some $$T(1)$$ times, the average regret acculumated there is $$T(1)\Delta_1$$, and we add it over all machines. The last step follows from previous step, by first exchanging the summation and than noticing that $$\Delta^\prime_i$$ and $$T(i)$$ are independent (i.e. $$\mathbb{E}[XY] = \mathbb{E}[X]\mathbb{E}[Y]$$). Here as our strategy picks each arm fixed number of time (equal to $$T/K$$) we can wrap up the regret as: $$\mathcal{R}_T = \frac{T}{K} \sum_i \Delta_i$$.

We see that this is linear in $$T$$. Can we do better than this? I.e. have the regret sublinear? One does get the feeling that this is not the best. After exploring for some tries, we need to dynamically update our method, and not just naviely keep pulling.

## 3. Naïve 2.0

Before actually addressing the deeper question of exploration, one can make some improvements to the naive. One can have a cutoff number, $$M$$ ($$\lt T/K$$), which is the maximum times we will pull any particular arm. We will thus pull the optimal arm (in so far indicated by statistical parameters) much more often (additional $$T - KM$$ times). Although what should be the cutoff number $$M$$ is unclear right now but good news is, with appropriate $$M$$, that regret will be sublinear (as a fact same as of UCB[^3]) in guassian with unit variance setting.

## Notes

[^1]: This horizon can be infinite too, for which we might use discounting for things to make sense. The reason why we aren't just considering the task of finding the best machine is simple - the naive algorithm can does that. Once we have algorithms that can learn, we would like to know which can learn the fastest or learn while still making huge rewards.

[^2]: Don't worry about the remainder if $$T \text{ mod } K \neq 0$$. For consistency we mean $$\lfloor T/K \rfloor$$. When $$T$$ is quite large compared to $$K$$, the last machine (which would be extra tries, equals to remainder) won't make others very upset ($$\lfloor T/K \rfloor \gg$$ $$T \text{ mod } K$$). If you want let $$T$$ be a multiple of $$K$$. For our regret calculation it doesn't make a differene, we can always consider the upper cieling of the fraction $$T/K$$ as the upper bound and floor as the lower bound, keeping the same order.

[^3]: Having same asymptotic regret doesn't make the 2 algorithms equal! There robustness also counts, from which we mean what if we change our concentration analysis assumptions (the unit variance guassian i.e). UCB is more robust because the equivalent tool to $$M$$ in UCB is set dynamically.

</div>
