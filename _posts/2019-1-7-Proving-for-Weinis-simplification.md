---
layout: post
mathjax: true
author: Long
title:  "Proving for Weini's simplification"
---
In gillespie algorithm there are two steps calculating "reaction time" and random choosing a "reaction" with the weight "reaction rate", but in Weini's code the two steps simplified as one by choosing "reaction" which have the minimum "reaction time". Here I'd like to prove Weini's simplification has correct probability distribution

$$
P_i = \frac{v_i}{\sum_j vj}
$$

where $v_i$ is the "reaction rate" of "reaction" $i$, $P_i$ is the probability the "reaction" $i$ being chosen.

## proving

First of all, let's see the definition of "reaction time"

$$
\tau_i = -\frac{log(r)}{v_i}
$$

where $r$ is a $(0,1)$ uniformly distributed random variable, such that we get the distribution of $\tau$

$$
F_i(\tau) = 1 - e^{-\tau v_i}.
$$

A "reaction" $i$  with "time" $\tau$ is chosen means that all the other "reaction time" is larger than $\tau$, the probability of which is

$$\prod_{j \neq i}(1-F_j(\tau))=\prod_{j \neq i} e^{-\tau v_j} = e^{-\tau \sum_{j \neq i} v_j}$$

So, the probability of $i$ being chosen can be calculated by integrating over $\tau$

$$
\begin{aligned}
    P_i &= \int_0^1 e^{-\tau \sum_{j \neq i} v_j} d F_i = -v_i \int_0^{\infty} e^{-\tau \sum_{j \neq i} v_j} e^{-\tau v_i} d\tau\\
    &=-v_i \int_0^{\infty} e^{-\tau \sum_{j} v_j} d\tau = \frac{v_i}{\sum_j v_j}
\end{aligned}
$$

QED.
