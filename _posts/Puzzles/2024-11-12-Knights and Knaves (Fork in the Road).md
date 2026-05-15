---
title: A Simple Knights and Knaves Puzzle (Fork on the road)
date: 2024-11-12 15:16:29 +05300
categories: [Puzzle]
tags: [puzzle, logical, mathematics]     # TAG names should always be lowercase
description: A simple logical puzzle from a class of puzzles involving interviewing one (or more) member(s) of truth tellers or liers clan. The identity of clan is not known. The aim is to get hold of an answer to some question.
math: true
---

<div class="custom" markdown="1" style="font-family: Verdana">

## 1. Problem Statement

There is a fork on the road, one path goes to the village and other to the jungle. There is a bystander, a member of one of the two clans, unknown to you - truth tellers and liers. How many minimum questions you need to ask to acertain the right path?

> Note: Please refrain from asking questions of factual knowledge. For example, whether 2 + 2 = 4? This is philosophicaly equivalent to asking whether this equation is correct: $$R_{\mu \nu} - \frac{1}{2} R g_{\mu \nu} + \Lambda g_{\mu \nu} = \frac{8 \pi G}{c^4} T_{\mu \nu}$$. The issue is the apriori assumption that the bystanders and the reader have some shared history, i.e. to say both will have the same truth value for some question. Thus for all purposes, even this question, my name is \<reader please insert your name\>, true or false? is the same.
{: .prompt-info}

## 2. Solution

When we ask the bystander some questions, say "Is this path the right one?", we observe the truth teller and liers given opposite answer always. This raises 2 observations - 

1. Is it always the case that truth tellers and liers have opposite answer?

2. If so, we can't acertain the right path in one query.

The former is wrong! There is a class of problems, "self-referential" in nature, for which they have the same answer. For example, "Are you a truth teller?". Both clan members will answer yes! In these, the problem invariable talks about the "self". As for second, it is easily proved. If you only ask question of kind-1 (for which both answer differently), and the fact that you don't know the truth value yourself (read the note), there is no way to tell which clan gave what answer, you have made exactly zero progress! This raises yet another questions - *Can you learn anything even by asking >1 non-referential questions?* Not really! For now all the question, standalone doesn't tell anything, due to 1-question reasoning. The only hurdle to generalize is: the identity of person answering remains same. I.e. say the next question truth value is related to truth value of a prior question, the answer of the bystander should be consistent. But this doesn't help either, bystander will just be consistent. A clean way to look is by viewing lier as a truth teller, but one who genuinely thinks the other path is correct (and conviently his truth table is the very opposite of our actual truth teller). For all purposes of non-referential nature, where we can't question on his self, and consider questions where lier truth value are surely opposite of truth teller, this viewpoint is right. Now you are always questioning a truth teller, and you don't know the truth. What are you even attempting at!! There is just no question you can ask, they both are equally true, and both paths are thus equally valid. This also has another consequence, all non-referential questions are essentially the same! As we don't know the truth value ourselves, all problem are the same. So this class of problem is summed up by one question, say, "Is this the right path?"!

Things are different for referential. As we see, liar is aware of the fact that he is a liar. Our truth teller facade fails to a simple question, "are you telling the truth"? Liar will answer yes, but then he would cease to be a truth teller who is just wrongly informed, for he is indeed rightly informed about himself. This tells us one thing, if there is a solution, we must make you of self-referential questions, as non-referential alone are (is!) insufficient.

Another observation, Does all referential questions hear same answer from truth teller and liars? Simple ones sure, if the question refers to nature of truth of the indiviual, the base truth value of the liar is opposite to that of the truth teller (unlike the usual case, where they share the same truth value), negation on top will make it the same. But one can compound referentials, like "Is your answer yes to, are you a truth teller?". Now both answer differently again. Here the second question ("Is you answer yes") refers former question ("Are you a truth teller"). As both liars have same truth value of this refered question ("Are you a truth teller"), they negate themselves again. If you add a third referential question, that references second question, now the they both share different truth value and there final answer would be same. So, a chain of referential question, where the next question only and only references prior question, in even length have opposite answers and for odd length same answer.

This begs the question, what happens when we compound non-referential and referential questions? Say we start with non-referential and the referential refers to that. Both clans differ on truth value of former and thus after reference, have same value. One can generalize however they like using this line of reasoning.

This very naturally leads to our solution! If you know the bystander is a truth teller, you can get the answer. The issue is being a liar. But if we only consider questions whose truth value is same regardless of the teller, we can assume the truth teller is speaking! *So what question, for which both types of bystanders give same answer and by which you can infer the direction?* Referential + non-referential of the form, "Is your answer yes to, is this the right path?". We already know both types will give same answer, so W.L.O.G assume it is the truth teller, and did you hear what he said? Yes, voilà take that path, if no, take the other one!! Call it one-shot or two-shot, your choice.

Final observation, are the questions whose truth value is different for both parties, any useful? This naturally lends itself into, what all questions can be asked. Here we only considered questions that build on top rather than say live parallely, like "Are you a truth teller xor is this the right path?". The question space is a bit interesting, don't you think? Answer to former doesn't look nice, atleast it looks to me as of writing, the question we consider are nice in the sense you change parity of any one question, the overall answer will come out reverse. However same is not necessarily true for question just described above. So in theory it is even possible that same question can have same or different truth value (for a truth teller or a liar), depending on truth values of questions (like answer to the question, "is this the right path"). It is like a function from boolean-tricky-space to boolean. Maybe some other day! Though if the overall question is changing parity when non-referential statement changes truth value, those questions are useless. For all the referential stuff is doign amass to nothing, it just acts as a simple map from either yes value of non-referential → yes value of overall question or no value of non-referential questions → yes value of overall question. Just changes the nature of truth teller to liar if the map is yes → no, and no change is yes → yes. As we don't know the truth value of our base question, they both are for our purposes truth tellers.

## References

1. Martin Gardners, "My best mathematical and logic puzzles", puzzle name: Fork in the road.

2. [Knights and Knaves Wikipidea page](https://en.wikipedia.org/wiki/Knights_and_Knaves)

</div>
