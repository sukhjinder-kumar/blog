---
title: A First Course in Reinforcement Learning (PENDING)
date: 2025-05-02 15:53:04 +05300
categories: [Computer-Science, Reinforcement-Learning]
tags: [comptuer_science, mathematics, probability, statistics, rl, mdp, dp, theory_course]     # TAG names should always be lowercase
description: In this introductory post we discuss the mathematical model of an MDP and some elementary ways to solve it in both offline and online setting.
math: true
image:
  path: /assets/img/RL/thumbnail.jpg
  alt: An image of an chess board with probability annotation for possible moves, given by an RL agent.
---

<div class="custom" markdown="1" style="font-family: Verdana">

## 1. The Mathematical Model

Reinforcement Learning is a technique used to solve, i.e. find an optimal strategy, a particular class of problem called "Markovian Decision Process". The problem is apt at modeling several of the real world situation which we associate with "learning from the environment". For example traffic, with time we get accustomed to the pattern and adjust our path so as to reduce our travel time. The key aspect is: interaction with the environment and learning from it (understanding its dynamics, and then logically using it to our advantage). The logically using part is theoretically done, there is not much to do (as we will see)[^1]. The central problem is understanding the dynamics of problem (which is random) and exploiting it. This too has to be done cleverly, one just doesn't sit for days to observe traffic (and failing to get paid for his job!) and then exploits. This is bad, first - well, it surely isn't optimal, second - who knows you set to observe on a very wrong and misleading day! In practice we balance the exploration and exploitation.

### 1.1 Markov Chain

Before we introduce the notion of MDP, we begin with its natural predecessor - a Markov Chain. 

## Notes

[^1]: That is to say, when we have full knowledge of the environment (MDP) we know the best strategy. In practice, along the lines of exploration and exploitation, how we use this knowledge can vary and so one might say it is not "done". Take what you will.

</div>
