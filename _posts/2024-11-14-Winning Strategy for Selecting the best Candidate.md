---
title: Winning Strategy for Selecting the best Candidate (PENDING)
date: 2024-11-14 18:44:13 +05300
categories: [Puzzle]
tags: [puzzle, logical, mathematics]     # TAG names should always be lowercase
description: A practical game theory problem that can help you select (probabilistically) the best candidate when interviewing. Spoiler - The first candidate is always rejected!
math: true
---

<div class="custom" markdown="1" style="font-family: Verdana">

## 1. Problem

There are $$N$$ slips, on each of which a number is written. They are arranged in a linear fashion. You can only pick them in order. I.e. Say you picked the first card, now you have 2 options - 

1. Either be content, or 
2. Pass it, and select the next one. And repeat these 2 options till you reach the last card. Which by construct will be your card.

The key is you can't go back! The task is to stop at the largest number out of all slips. One must have forsight that a better card is not going to appear ahead, and not stupidly ignore the best card in hope of a better one.

This is equivalent to selecting best candidate in an interview, one can assign some numerical score (the score actually doesn't matter!) as to how good they are. You can either select or reject, and being a man of your word you don't go back. You have to maximize your chances of selecting the best candidate. The same interpretation goes for selecting spouse for marriage!

> Note: This is not same as maximize your expected score, rather maximizing probablity of selecting the best score.
{: .prompt-info}

The game is afoot, and you have to find the best strategy! 

> Note: This might appear spooky at a glance, but all we are actually asking is when should you stop trying for better. Like stopping at first is very bad, for it is only $$\frac{1}{n}$$ likely to be best. One can get better score than first simply by picking the next greater than firsts' score. You can always pick better as long as first is not the best, i.e. with probability $$1 - \frac{1}{n}$$ you get better score that naviely stopping at first.
{: .prompt-info}

## 2. Solution

The problem is equivalent to asking which of the following strategies is the best - Call the strategy of stopping at first - $$S_1$$, strategy of stopping at first greater than first - $$S_2$$ (the naive improvement over $$S_1$$ described in our note), similarly $$S_3$$ be ignoring the first greater than firsts' score, and selecting the first score which is greater than this new best,and so on till $$S_N$$. All we are saying is how many times you want to gamble before settling. 1 being no gamble, 2 being one time gamble (you drop your first card and look for a greater, and stop thereafter), 3 being you gamble twice (you pick first, drop it, find another number bigger than that and drop that too, and find another which is still bigger than the second and keep it) and so on.

Sometimes you won't be able to execute the strategy, as we saw if one gets the best score in first try, then there won't appear a better score and hence first bigger than first won't ever appear, and hence $$S_2$$ won't "run". In this by construct we have to pick the last card, which by condition is lesser, and we loose. So no executing strategy is equivalent to losing. This is one obvious downside of using these numbered strategies. Probabilistically the more the chances of these happening, the worse our strategy is. Thus it intuitively makes sense than best strategy is somewhere in the middle, not $$S_1$$ or $$S_N$$! As a fact, you almost always fail to execute $$S_N$$, for only $$\frac{1}{n!}$$ times you pass, which being when scores appear in ascending order. This is much worse than $$S_1$$.

Let us now compute probability of winning following these numbered strategies. As we already saw for $$S_1$$, probability of getting the best score is $$\frac{1}{n}$$. For $$S_2$$ it is slightly involved - 


</div>
