---
title: Green Eyed Dragon
date: 2023-04-06 16:25:10 +0530
categories: [Puzzle]
tags: [puzzle, logical]     # TAG names should always be lowercase
summary: This is a very innocent looking puzzle which makes absolutely no sense until it does!
excerpt_card: This is a very innocent looking puzzle which makes absolutely no sense until it does!
---

## Problem

---

You visit a remote desert island inhabited by one hundred very friendly dragons, all of whom have green eyes. They haven’t seen a human for many centuries and are very excited about your visit. They show you around their island and tell you all about their dragon way of life (dragons can talk, of course).

They seem to be quite normal, as far as dragons go, but then you find out something rather odd. They have a rule on the island that states that if a dragon ever finds out that he/she has green eyes, then at precisely midnight at the end of the day of this discovery, he/she must relinquish all dragon powers and transform into a long-tailed sparrow. However, there are no mirrors on the island, and the dragons never talk about eye color, so they have been living in blissful ignorance throughout the ages. 

Upon your departure, all the dragons get together to see you oﬀ, and in a tearful farewell you thank them for being such hospitable dragons. You then decide to tell them something that they all already know (for each can see the colors of the eyes of all the other dragons): You tell them all that at least one of them has green eyes. Then you leave, not thinking of the consequences (if any). Assuming that the dragons are (of course) infallibly logical, what happens? If something interesting does happen, what exactly is the new information you gave the dragons?

## Beauty

---

The most amazing aspect of this problem is why should something happen, as a bystander no new information has been passed on. Atleast so it seems!

## Solution

---

1. Say there is just one dragon, than trivially you just told him the color of his eye and boom by midnight he becomes a sparrow

2. Now say there are 2 dragons. Let us call them d1 and d2. From POV of d1, d2 is green (he can see), and night passes nothing happen. But there is a problem, it is trivial that d1 didn’t became sparrow but why didn’t d2 became sparrow. Cause you were green eyed too, else he would have known he is sparrow. This implies that after one day, when the other doesn’t become sparrow you realize that you are also green. 

3. Now just for creativity sake imagine 3 dragon, d1, d2 and d3. Also note to shorten the implication we would use symmetry of POV’s, you will see what it means. From d1 POV, say you are not green eyed. What happens now to both of them. From n = 2 case we would likely see that they realize after 2 days they are green and would become sparrow (on midnight of 2nd day). But that doesn’t happen, and the only reason it doesn’t is because you are green. Cause otherwise they would. (A ⇒ B is logically equivalent to not B ⇒ not A. Here A being non-green color and B being becoming sparrow after 2 days)

4. Now we have the machinary to show that n dragon would become sparrow after n days. We will use induction, we know the result is true for n = 1. Assume it is true for any random n. Now in case of n+1 dragons. From POV of d1, if he was non-green, the rest of n dragon should become sparrow after n days. But it doesn’t happen, and this implies that d1 is green eyed. And becomes sparrow on n+1 day. By symmetry of POV, all dragon become sparrow by n+1 days. Hence by induction our result is true for all n ≥ 1.

According to the new information added is synchronization of thoughts. At the very moment d1 knows that d2 knows … dn know that atleast one of them is green eyed. The very fact that all of them are concerned makes the thing work. Cause they become sparrow if they know, if they just ignore it then they will live happily. As an extension if one of them didn’t hear your farewell (or specifically the ‘atleast one green-eyed dragon’ part) there would still be dragon. Cause the chain of reasoning won’t complete, just consider n = 2. If d2 just don’t care, the fact that he is not sparrow doesn’t imply anything, it is just didn’t care to hear the announcement. For n = 3, using same LOR (line of reasoning) d1 becomes bystander and await outcome of d2 and d3, but here using prior argument for n = 2, no disturbance is created, as d2 has no way of knowing whether he is green.

## Reference

---

I found this problem in the book, "The Green-Eyed Dragons and Other Mathematical Monsters" by David Morin. The solution given by him, almost identical to above is uploaded [here](https://www.physics.harvard.edu/files/sol2.pdf).
