---
title: Generalized Binary Search (PENDING)
date: 2025-02-06 21:05:13 +05300
categories: [Computer-Science, Algorithms]
tags: [pending, mathematics, computer_science, binary_search, algorithms]     # TAG names should always be lowercase
description: In this post we show the optimality of the worst case time complexity of binary search and see how to adapt binary search to a setting when the elements aren't equally likely present in the array.
math: true
---

<div class="custom" markdown="1" style="font-family: Verdana">

## 1. Binary Search 

Consider the problem of searching from an sorted array (with distinct elements). What is the fastest and most efficient way to do so? The naive searching, one by one, sets the lower bound for worst case time complexity with $$\mathcal{O}(N)$$ where $$N$$ being the array length. Here the space complexity is constant. We can do a whole lot better by using the "sorted" property. Binary search algorithm improves the worst case time complexity to $$\mathcal{O}(\log N)$$. We proceed first by writing the algorithm and then proving time complexities for the best, average and the worst case scenario. After this we will show that the binary search achieves the best worst case time complexity for searching from an sorted array!

The algorithm is as follows -

1. Set $$l \leftarrow 0$$ and $$u \leftarrow N-1$$.
2. If $$l > u$$ terminate. If not, check if our key is present at index $$k = \lfloor (l + u)/2 \rfloor$$. If present return the index otherwise proceed.
3. If our key is $$\gt$$ key at index $$k$$ then update $$l \leftarrow k$$. If our key is $$\lt$$ key at index $$k$$ then update $$u \leftarrow k$$. 

## Problem Statement

The standard binary search involves, at each time step, in a sorted array, partitioning the array into 2 halves about the middle number and pruning one of them based on the fact whether our search number is greater or less than the middle number. 

1. First why split in the middle only? 

2. Imagine the array has duplicates is the middle still the best? A better way to formulate our problem is using probability - ...

</div>
