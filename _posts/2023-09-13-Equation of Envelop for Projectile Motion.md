---
title: Equation of Envelop for Projectile Motion 
date: 2023-09-13 15:11:20 +0530
categories: [Physics]
tags: [physics, kinematics]     # TAG names should always be lowercase
summary: In this blog post we are going to find the equation of the envelope for a projectile motion. We will find maximum range and corresponding angle when object is lauched from an elevated surface.
excerpt_card: We are going to find the equation of the envelope for a projectile motion, maximum range and corresponding angle when object is lauched from an elevated surface.
math: true
---

<div class="custom" markdown="1" style="font-family: CMS"> 

## 1. Basic Theory

You might know the angle for which range is maximum on level ground, namely $45^{\circ}$.
Notice that this is independent of the velocity! For those who haven't seen this here is
the little proof -

$$
\begin{align*}
    R & = v_x \times time \\
	R & = v\cos\theta \times \left( \frac{2v\sin\theta}{g} \right) \\
\end{align*}
$$

Here we can calculate time using $S = ut + 1/2at^2$, where acceleration is $g$, $S$ is 0
as starting and final position is same, and $u$ is $v\sin\theta$.

$$
    R = \frac{v^2 \sin 2\theta}{g}
$$

Clearly $\sin$ is maximum at $90^{\circ}$, giving $\theta = 45^{\circ}$

## 2. Main Course

Now we alter the problem slightly. Instead of a level surface we launch the ball from a cliff.
What is angle that corresponds to maximum range for a projectile when you throw the object 
(with velocity $v$) from a cliff ($h$ height from surface)?

Before going any further let me comment on one certainity, it will be $\to 0^{\circ}$! Why you
may ask. The idea is horizontal throw ($\theta = 0\degree^{circ}$) has the most horizontal velocity.
The only reason why it doesn't correspond to max range is due to time of flight. However when you
introduce a cliff, every throw gets some time in the downfall. Let us for sake of all non-zero angle 
throws, say downfall time from cliff to ground is same. This is wrong as all other throws (except 
$0\degree$) have some non-zero downward velocity, but let us be generous to them. Apart from this 
is constant time, all other also enjoys time taken during the parabolic arc above the cliff. Let 
us say all takes time corresponding to $90\degree$, i.e maximum time of flight. The idea is even 
in best case total time, the ratio of time of parabolic arc above cliff and time in downhill tends 
to 0! The reasoning being former is constant (function of velocity) whereas later increases with 
height of cliff. Now when we compute range, it will be $v_x \times$ TotalTime. Total time is 
something very large + something constant (and hence small). Multiplied by $v_x$ yeilds

$$
\begin{align*}
	R(h) & = v_x \times (t_{parabolic \ arc} \ + \ t_{downhill}) &\\
		& = v_x \times (constant \ + \ t_{downhill}) &\\
		& = v\cos\theta \times constant \ + \ v\cos\theta \times t_{downhill} &\\
		& = constant^\prime \ + \ v\cos\theta \times t_{downhill}
\end{align*}
$$

Compared to horizontal throw 

$$
	R(h) = v \times t_{downhill}
$$

Clearly for sufficiently large h, or concretely large $t_{downhill}$, for every $\theta$ we will have Range for horizontal throw > Range for inclined throw. 

$$
\begin{align*}
	v \times t_{downhill} > constant^\prime \ + \ v\cos\theta \times t_{downhill} \\
	v \times t_{downhill} \times (1-\cos\theta) > constant^\prime \\
	constant^{\prime\prime} \times t_{downhill} > constant^\prime
\end{align*}
$$

In above everything is constant, only $t_{downhill}$ depends on $h$. For large $t_{downhill}$ above inequality is trivially satisfied. Above calculation might seem elaborate but in essence what we showed is every throw gains some constant horizontal distance in its above the cliff parabolic arc. However as $v > v\cos\theta$,  after some $h$ that little increment faids away, and the relative difference in velocity catches up to that initial gain. It is like 2 car racing one with velocity $v$ and other with $v\cos\theta$, later having a head start of say some distance $x$. It is just matter of time when faster catches it up![^1] 
Using same analogy one can say after sufficient height, every throw will surpass throw that is launched at higher angle to it! I.e $30\degree^{circ}$ after some point will surpass $60\degree$. I don't know how to put the intuition more concretely but there is a strong urge to claim that $\theta$, corresponding to maximum range, will decrease monotonically till $0\degree$.

Now let us come back the original problem of actually finding the angle.

## 3. Further Problems

What is the equation of envelope for both level surface and from a cliff. Imagine all possible throws, what is the region where you the ball can't reach. 

Say you have a sprinklers. tossing water uniformly at all angles in all direction (symmetry in 2D surface). Now what is the density of water w.r.t to radial distance from centre. I.e there will be angles for which range doesn't change much, there water will log more compared to angles for which slight change results in greater range change. Say water log is inversely proportional to $dR/d\theta$, you can understand this by assuming that sprinklers releases water in little bursts of mass $dm$ (or some volume $dv$). The entire mass is collected at $R(\theta,h)$. After a very long time, we would like to see radial strips which have higher water log. Water log in $dR$ would be $dm \times$
Above needs some modelling. We might need to consider $dm$ mass is being pushed in $d\theta$ angle.

## 4. Resources and Further Reading

1. [IB Maths Resources](https://ibmathsresources.com/2020/04/06/envelope-of-projectile-motion/#:~:text=Finding%20the%20equation%20of%20an%20envelope%20for%20projectile%20motion&text=F(x%2Cy%2Ctheta,F%20with%20respect%20to%20theta.))
2. [Stack overflow: Envelope of Projectile Trajectories](https://math.stackexchange.com/questions/1495086/envelope-of-projectile-trajectories)
3. [Envelope of Family of Angled Projectiles and Its Universal Geometric Characteristics by Haiduke Sarafian](https://www.scirp.org/pdf/ajcm_2020090315280603.pdf)
4. [On the Geometrical Approach to Projectile Motion by Philip Robinson](https://www.jstor.org/stable/pdf/3620177.pdf?refreqid=excelsior%3A371a5f352e9d301ff2fde324e3de6028&ab_segments=&origin=&initiator=&acceptTC=1)
5. [Wikipedia: Parabola of Safety](https://en.wikipedia.org/wiki/Parabola_of_safety)
6. [Butikov, E. I. (2003). Comment on  The envelope of projectile trajectories . European Journal of Physics, 24(4), L5–L9. doi:10.1088/0143-0807/24/4/101](https://iopscience.iop.org/article/10.1088/0143-0807/24/4/101/meta)
7. [Mihas, P. (2019) Envelopes, Foci, and Maxima of Special Trajectories. American Journal of Physics, 87, 836.](https://doi.org/10.1119/1.5122894)
8. [No Calculus Needed?! How to Maximize Range Using Simple Geometry, YouTube Video by MathyJaphy](https://www.youtube.com/watch?v=xwhbT9Do1RQ)
9. [The Envelope of Projectile Trajectories, YouTube video by Elliot Nicholson](https://www.youtube.com/watch?v=P32zK3I8dog)
10. [Stack overflow for maximum range and angle when lauched from elevated surface](https://math.stackexchange.com/questions/127300/maximum-range-of-a-projectile-launched-from-an-elevation)

---

[^1]: Just a subtle point the cars are accelerating. But as accelerating is same, there relative velocities remain the same! So no difference in time of convergence.

</div>
