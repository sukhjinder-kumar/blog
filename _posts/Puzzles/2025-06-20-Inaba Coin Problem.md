---
title: Inaba Coin Problem
date: 2026-05-15 15:45:35 -0500
categories: [Puzzle]
tags: [puzzle, logical, mathematics]     # TAG names should always be lowercase
description: You have 10 points distributed on the plane, can you cover them using unit disks without any overlap.
math: true
---

<div class="custom" markdown="1" style="font-family: Verdana">

## 1. Problem Statement

Consider 10 points, $$\{a_i\}_{i=1}^{10}$$ with $a_i \in \mathbb{R^2}$. Can you cover them using units disks s.t no 2 disks overlap.

## 2. Proof

For number of points 1, 2, and 3 things are easy to proof (one can explicitly tell where the disks should be). It is a bit tricky to move forward from purely geometric viewpoint.

Here a few observations one makes in the due process -

1. If we change the question into unit squares instead of disks, we can find the configuration of squares (namely the square grid![^1])

2. Same logic works for any polygon that completely tiles the plane. Unfornutately, from angle consideration[^2], pentagon can't, hexagon can and nothing after that does. In particular circle doesn't and has a (basic geometric assertion) packing percentage of 90.69%.

We will now use a probabilistic method. Fix the circular packing, we want to show for $n = 10$ we can always nudge so that they lie in the grid. From nudge we can mean moving the origin of this grid to someplace else.

Let $$Z = \{[v] \mid v.(\text{grid}) \neq \text{grid}\}$$ be the set of all vector that produce a different grid[^3]. Let $Z_i \subseteq Z$ that puts $a_i$ outside the grid (i.e. bad nudges for $a_i$). We want to show $\cup Z_i \neq Z$.

Now the key step: If we can show $\text{Prob}_{z \sim \text{uniform}(Z)}(z \in \cup Z_i) < 1$[^4], it would mean the set $Z - \cup Z_i$ has measureable size, in particular non-emtpy. 

We know $\text{Prob}(\cup Z_i) \leq \sum_i \text{Prob}(Z_i)$, with equality if sets (events) are disjoint. Here $\text{Prob}(Z_i)$, is probality a random nudge in our $Z$ will push $a_i$ out. First the probability is independent of $i$. Second, one can switch the label to say move $a_i$ instead of grid. And then we realize it is same as saying just pick $a_i$ and drop it back again in the grid (within the region achievable by vectors in $Z$). One can convince this is just the ratio of area of uncovered area in optimal packing over total area. Or percentage of area uncovered, which as we said is 9.31% (100 - 90.69). I.e. $\text{Prob}(\cup Z_i) \leq n (0.0931)$, and we set this $< 1$ to get $n < 1/0.0931$ giving $n < 10.74$. I.e. $n \leq 10$ satisfies our relation and we have proved our claim.

This technique can be applied in any dimension, but optimal packing percentage of spheres drops very quickly and one can only prove this result for very small $n$'s (has to be better than the trivial lower bound of $n \geq 3$) and after a few dimension it is useless.

## 3. Remarks

The lower bound for maximum points that can be put in a plane and still be coverable by non-overlapping disks has been pushed to $\geq 13$ and upper bound 
$\leq 50$.[^5]

## Footnotes

[^1]: I.e. Draw the square grid and each point will lie in some unit square. It might happen the point lies on the boundary, you can easily convince for finitly many one can come up with a tiny nudge that sorts everything out. Otherwise the set of this configuration of points has 0 measure and just ignore them.

[^2]: Consider the vertex of any cell in the tiling. The angle, in the regular gon, of that vertex has to divide $360^\circ$ (a bunch of other gons attach to it with same angle, and they add upto $360^\circ$). One gets our claim from there quickly.

[^3]: From $v.(\text{grid})$ I meant move the origin of grid to $v + \text{origin}$. For example if you move the origin by integer unit right/left you will basically be translating the grid by that amount and visually nothing will change. Its like a symmetry. And we are modding out by those. That is collection of vector that produce a different grid. Easy to see this is measureable (as a fact equal to all vectors in the hexagon formed by 6 attaching circles covering the origin circle)

[^4]: Fancy way of writing ratio of areas.

[^5]: Refer to the following research paper [Covering Points with Disjoint Unit Disks](https://2012.cccg.ca/papers/paper13.pdf).

</div>
