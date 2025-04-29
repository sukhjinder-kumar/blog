---
title: Pursuit Problem (PENDING)
date: 2025-04-01 10:15:02 +05300
categories: [Physics, Kinematics]
tags: [physics, kinematic, relative_motion, puzzle]     # TAG names should always be lowercase
description: A elementary kinematic problem that requires one to understand difference between radial and perpendicular velocity.
math: true
mermaid: true
---

<div class="custom" markdown="1" style="font-family: Verdana">

## 1. Problem-1 Statement

Consider a simple setup, an individual is stationed at each of the vertex of a N-sided regular polygon. From t = 0, they are always moving towards the next person. When will they all meet, and what is the path followed by any one of them?

## Solution

Before we begin, we must realize one simple idea - Radial and perpendicular velocity. Consider 2 particles A and B, A be at rest and B be moving at velocity $$v_x$$ and $$v_y$$ (as shown below). 

![Radial and Perpendicular Velocity](/assets/img/PursuitProblem/radial_tangential_velocity.png)

Here $$v_x$$ is always radial to the line AB and $$v_y$$ is always tangential to the line AB. The distance between A and B is only affected by $$v_x$$ and not $$v_y$$! On surface one might say $$v_y$$ does alter the distance, using some notion of pythagorian equality, but one should note $$v_y$$ is "always" perpendicular to the line AB. Its like the velocity of a ball being hurled in a circle, it would have added distance if it kept moving (even if for a moment) but rather it is always changing just like in a circle.

Let us consider the case of an equilateral triangle ABC. Let us first find the time of collision (by symmetry which will occur at the very center, a point symmetric w.r.t all). A is moving towards B with velocity $$v$$ and B is moving towards C with the same velocity. Let us see the situation from reference frame of A, B is effectively moving towards A with a velocity $$v + v \cos (\pi/3)$$, which is $$3v/2$$. This is but for that very instant. But owing to symmetry, one can easily see the triangle ABC after a $$\Delta t$$ interval is also an equilateral triangle[^1], thus this is always the radial velocity. So the time of collision would be $$s / (3v/2)$$ $$= 2s/3v$$. For a general N-sided regular polygon, it would be $$s / v[1+\cos((N-2)\pi/N)]$$, where $$s$$ is the side length. As a special case, let us see what happens at N = $$\infty$$, i.e. a circle. The time becomes infinite! Which makes sense, as the pursuer and the chased point are always at $$\pi$$ angle w.r.t to each other, there motion is just rotation in the circle.

The path followed is quite intutive to visualize, for the regular 4-gon following is the trajectory.

![Pursuit Problem trajectory on a Square](/assets/img/PursuitProblem/Four_point_pursuit_curve.gif)
_Pursuit Problem trajectory on a Square. Ref: https://en.wikipedia.org/wiki/Pursuit_curve_

## 2. Problem-2 Statement

Let us a consider a 2 player pursuit problem where we can derive the equation for the curve easily. Let A and B be 2 points on the plane. A starts moving along a straight line at a constant velocity $$v_A$$ (A never deviates from the first chosen direction). B is the pursuer, and is constantly changing the direction as to follow A, with velocity $$v_B$$. What is the time of collision, where does the collision takes place and what is description of path traced by B.

## Solution

Following image shows visually our situation (replace P with B). B is always moving towards A and A is moving nonchalantly along a straight line.

![A simple pursuit curve in which P is the pursuer and A is the pursuee](/assets/img/PursuitProblem/Radiodrome-simple-y-bw.png){: w="250" h="400"}
_A simple pursuit curve in which P is the pursuer and A is the pursuee. Ref: https://en.wikipedia.org/wiki/Pursuit_curve_



## Notes

[^1]: What else could it be? All angles and sidelengths have to be the same because of symmetry in there motion.

</div>
