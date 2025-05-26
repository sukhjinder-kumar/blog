---
title: Generalized Binary Search (PENDING)
date: 2025-02-06 21:05:13 +05300
categories: [Computer-Science, Algorithms]
tags: [pending, mathematics, computer_science, binary_search, algorithms]     # TAG names should always be lowercase
description: How to adapt binary search to a setting when the elements aren't equally likely present in the set.
math: true
---

<div class="custom" markdown="1" style="font-family: Verdana">

## Big-O Notation

## Binary Search

Consider the problem of searching from an sorted array (with distinct elements). What is the fastest and most efficient way to do so? The naive searching, one by one, sets the lower bound for time complexity with $$\mathcal{O}(N)$$ where $$N$$ being the array length. Here the space complexity is constant. We can do a whole lot better by using the "sorted" property.

## Problem Statement

The standard binary search involves, at each time step, in a sorted array, partitioning the array into 2 halves about the middle number and pruning one of them based on the fact whether our search number is greater or less than the middle number. 

1. First why split in the middle only? 

2. Imagine the array has duplicates is the middle still the best? A better way to formulate our problem is using probability - ...

</div>
