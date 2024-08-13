---
title: Fast Modulus calculate of power of 2 and pow2 - 1
date: 2024-08-13 11:36:38 +05300
categories: [Programming, Mathematics]
tags: [programming, number_theory, mathematics]     # TAG names should always be lowercase
description: In this post we will learn how to efficiently calculate modulus w.r.t power of 2 and pow2 - 1.
math: true
---

<div class="custom" markdown="1" style="font-family: Verdana"> 

## 1. Modulus with power of 10s

Consider numbers like 12, 14, 17, what is the modulus 10? 2, 4 and 7, rather quick of you! What we just did is, picked the unit digit. Technically, we imagined the number as breakdown into, there natural decomposition or "meaning", 10 + 2 / 4 / 7. And we use the fact that $(a + b) \text{ mod } c = (a \text{ mod } c + b \text{ mod } c) \text{ mod } c$, or for such a trivial case, just divided mentally, all proper tens go away and unit is the only remain. 

Say we want to compute $n \text{ mod } 10^s$, we just read the $s$ least significant digits. For example, 123 mod 100 = 23, read 2 ($10^{\boxed{2}}$) least significant digits. All the multiples of powers 10 > $10^2$, perfectly divide (in our mental calculations) and first 2 digits is all that remains.

## 2. Modulus with power of 2s

This follows naturally from our above discussions. Say numbers are given in there binary format (like 7 = 111, 10 = 1010), you should read it just like the base of 10 (as in 1010 to be read as $1 * 2^3 + 0 * 2^2 + 1 * 2^1 + 0 * 2^0$). Nothing has changed except the way we label a number. 2 is equivalent to 10 for our purposes, and as such modulus of $2^s$ is given by $s$ least signinficant bits. For example, 10 or 1010 in binary mod $2^3$ (8) is given by 010 = 2. (Think about it!)


## 3. Modulus with a pow2 - 1

Consider numbers of the form $2^s - 1$. For example 7 which can be written as $2^3 - 1$, which is also a mersenne prime. How to calculuate mod w.r.t it, of course without explicit integer division, which can be time consuming in terms of number of logic gates used? The idea is simple, we know how to get remainder under power of 2, and we can extrapolate the error in considering power of 2 instead of one off from it. Basically, $n = 2^p * Q + r$, which can be written as $ = (2^p - 1) * Q + (Q + r)$. I.e. quotient + remainder of 2^p are equivalent in terms of mod (if Q + r > $2^p$ - 1, take mod from it too). So if somehow we are able to get remainder and quotient, we are done! The remainder is easy, just read s least significant digits. The quotient is even simpler read remaning bits. For example what is quotient of 21 divided by 10, its 2, as 2*10 + r / 10 = 2. Any $a_{n} a_{n-1} a_{n-2} \cdots a_s \cdots a_1$, when divided by $10^s$ can be written as $a_{n} a_{n-1} \cdots a_{s+1} * 10^s + a_s \cdots a_1$, which when divided by $10^s$ (definition at this point of quotient) gives $a_{n} a_{n-1} \cdots a_{s+1}$ as the quotient. As base 2 is logically equivalent to 10, same holds for it. To calculate quotient w.r.t to power of $2^s$ read all the digits after first s digits. Like (11) 1011 / 2^2 gives quotient as 10 (2) and remainder 11 (3). Consequently, 1011 mod 2^2 - 1 will be Q + r = 2 + 3 = 5 or take further mod with 3 = 2.

There is a fancy way to do our calculuations in programming languages. To read first s least significant digits do `n & (2**s-1)`, as $2^s - 1$ will be nothing but a string of 1s (of length of s, preceded by a padding of 0 in more significant places), and taking *AND* operator would return the first s digits of our original number (think!). To remove first s digits and get remaining, we can use `n >> s`, like 1011 >> 2 would return 10, just drops first 2 bits. The former gives quotient under $2^s$ and later gives us the remainder under $2^s$, add and you get modulus with $2^s - 1$

```py
def mod_power_2_minus_1(n, s):
    p = 2**s - 1
    i = (n & p) + (n >> s)
    if i > p:
        return i - p
    else:
        return i
```

Just note that it is possible that i is >> p, true for small ps, where quotient is very large. Here you have to call the function recursively. We are returning i - p just to avoid one step recursion cost, that is all.

</div>
