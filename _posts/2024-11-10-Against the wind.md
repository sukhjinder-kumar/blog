---
title: Against the wind
date: 2024-11-10 15:16:29 +05300
categories: [Puzzle]
tags: [puzzle, logical, mathematics, physics]     # TAG names should always be lowercase
description: Say you commute from A to B, and back from B to A, in a straight line. Will your travel time be any different if a constant wind is blowing from B to A?
math: true
---

<div class="custom" markdown="1" style="font-family: Verdana">

This is a rather simple puzzle, which I found in Martin Gardners' My best mathematical and logical puzzles. The reason this is interesting is for some reason one just guesses the time will be the same! The reasoning goes like : the "effects" of wind cancels out, the "something" gained in back journey from B to A is lost in forward journey from A to B. Sounds all good, but this is wrong. As a fact total time will be greater. 

Before showing how, one must note, say you are travelling in some direction with some speed. Now wind starts blowing in your favor with constant speed (call u). The distance you cover will now increase by ut, this is the distance provided to you by the wind. 

In our example, the only difference is time is not fixed, rather distance. What happens is, in forward journey, as wind is opposing you, means overall ahead time increased, the effect of wind last longer. In backward journey, as wind is supportive, meaning overall backward time decreased, the effect of wind last shorter. The round trip time would have been same iff the effects of wind acted for same time. But here we see supportive time is less and counter productive time is more. So overall it takes more time for the round trip.

One can see the same conclusion with basic kinematics - $t$ is the total round trip time, $v$ is your speed, and $u$ is the wind speed blowing from B to A.

$$
\begin{align*}
    t &= t_{\text{AB}} + t_{\text{BA}} \\
      &= \frac{d}{v-u} + \frac{d}{v+u} \\
      &= \frac{2dv}{v^2 - u^2} \\
      &= \frac{2d}{v(1-u^2/v^2)} \\
      &\gt \frac{2d}{v}
\end{align*}
$$

This result holds true even if wind is blowing A to B instead of B to A, or the path we took is not straight. All we care is wind should be tangential, favourable (non-favourable) while returning (going) and constant, and time will be greater.

</div>
