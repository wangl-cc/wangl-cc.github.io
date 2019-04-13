---
layout: post
mathjax: true
author: Long
title:  "Host-parasite dynamics:Part 1"
---

Here I'd like to write a series of articles to introduce some model about Host-parasite dynamics. This article is the first one, which will introduce the basic model of Host-parasite dynamics.

## Basic model

The basic epidemiological dynamics of a host-parasite interaction can be described by the following system of ODEs:

$$
\begin{array}{l}
\dot{x} = k - u x - \beta x y \\
\dot{y} = y (\beta x - u - v)
\end{array}
\tag{1}\label{e1}
$$

Uninfected and infected hosts are denoted by $x$ and $y$. The uninfected host population is regulated by a simple immigration-death process with constant immigration rate $k$ and death rate $u$. The infected hosts transmit the parasite to uninfected host at rate $\beta x y$ and die at the increased rate $u + v$, where $v$ defines the virulence[^1] of the infection.

Although this model ignored many important complications, this model will help us to understand some important feature of host-parasite dynamics. At \eqref{e1} there are two equilibriums

$$
\left\{
\begin{array}{l}
x^* = \frac{k}{u}\\
y^* = 0
\end{array}
\right.
\text{and}
\left\{
\begin{array}{l}
x^* = \frac{u + v}{\beta}\\
y^* = \frac{\beta k - u (u+v)}{\beta (u + v)}
\end{array}
\right.
$$

which one is stable the other is not. The stability of equilibriums depends on the value  of

$$
R_0 = \frac{\beta}{u + v} \frac{k}{u} \tag{2}\label{e2}
$$

which defines the basic reproductive ratio. If $R_0 < 1$ the stable equilibriums is the former, else the latter.

The basic reproductive ratio can be understand as follows. The ${1}/{(u + v)}$ is the average lifetime of an infected host. The ${\beta}/{(u + v)}$ is the average number of new infected hosts caused by a single infected host. And the ${k}/{u}$ is the equilibrium of uninfected hosts population. Hence equation \eqref{e2} represents if the parasite can invade equilibrium of uninfected population.

## Model with more than one parasite

For single parasite strain model, there is not competition. The evolutionary trend of virulence cannot be represent. Without the loss of generality, we consider the two parasite strains model

$$
\begin{aligned}
\dot{x} &= k - u x - x (\beta_1 y_1 + \beta_2 y_2)\\
\dot{y_1} &= y_1 (\beta_1 x - u - v_1)\\
\dot{y_2} &= y_2 (\beta_1 x - u - v_2)
\end{aligned}
$$

The basic reproductive ratios of two strains are, respectively, given by

$$
R_{0, 1} = \frac{\beta_1}{u + v_1} \frac{k}{u}
$$

and

$$
R_{0, 2} = \frac{\beta_2}{u + v_2} \frac{k}{u}
$$

Only if the $R_{0, 1} = R_{0, 2}$, two strains can coexist, which is not generic. If $R_{0, 1} \neq R_{0, 2}$, there are three equilibriums:

$$
E_0: \left\{
\begin{array}{l}
x^* = \frac{k}{u}\\
y_1^* = 0\\
y_2^* = 0
\end{array}
\ 
\right.
E_1: \left\{
\begin{array}{l}
x^* = \frac{u + v_1}{\beta_1}\\
y_1^* = \frac{\beta_1 k - u (u + v_1)}{\beta_1 (u + v_1)}\\
y_2^* = 0
\end{array}
\right.
\ 
E_2:\left\{
\begin{array}{l}
x^* = \frac{u + v_2}{\beta_2}\\
y_1^* = 0\\
y_2^* = \frac{\beta_2 k - u (u + v_2)}{\beta_2 (u + v_2)}
\end{array}
\right.
$$

The stability depends on both $R_{0, 1}$ and $R_{0, 2}$. The strain with higher reproductive ratio will outcompete if $R_{0, 1} > 1$ and $R_{0, 2} > 1$. The other case, it's obvious.
Hence the evolutionary stress prefer the strain with higher reproductive ratio which is a crucial concept of epidemiology.

Notice, if there are no trade-off between $\beta$ and $v$ or any other condition, the virulence tends to be avirulent, which is a traditional view.

[^1]: Virulence have many different definition. Here virulence is defined as the parasite's effect on reducing the fitness of infected host.
