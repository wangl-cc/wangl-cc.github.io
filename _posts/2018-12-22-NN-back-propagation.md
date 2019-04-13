---
layout: post
mathjax: true
author: Long
title:  "Derivation of back propagation equation"
---

Following the Nielsen's book--["Neural Networks and Deep Learning"](http://neuralnetworksanddeeplearning.com/), I wrote a [Multilayer Perceptron (MLP)](https://github.com/wangl-cc/NeuralNetwork.jl) with julia to recognize handwritten digits in MNIST data, where I use the pkg--[JuliaDiff/ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl) to support different loss function but it doesn't work on activation function because there are something wrong to calculate the derivative of sigmoid function. Here I'd like to share my derivation of back propagation equation. All tensor (vector, matrix and any other tensor of higher rank) in this article follow the [Einstein notation](https://en.wikipedia.org/wiki/Einstein_notation), which means that any repeated indices except $l$ (which not means a rank in our tensor but its label, so the superscripts is labels and subscripts is indices.) implies summation of that term over all the values of the index ,and the $\delta_{ij}$ is a tensor we called [Kronecker delta](https://en.wikipedia.org/wiki/Kronecker_delta) which have properties:$\frac{\partial x_j}{\partial x_i} = \delta_{ij}= \delta_{ij}$ and $\delta_{ij}x_j = \delta_i$.

What is an neural network? Instead of the author of "NNDL" who think the network as a gate circuit, in my opinion the network is a series of linear regression:

$$a^l_i = \sigma(W^l_{ij} a^{l-1}_j + b^l_i).\tag{b0}\label{b0}$$

The main different between neural network and linear regression is the activation function, which I think is the reason why neural network is neural network.

The equation \eqref{b0} is an elegant equation, but for convenience of following discussion I divide it into two part:

$$
\begin{aligned}
    a^l_i =& \sigma(z^l_i) \\
    z^l_i =& W^l_{ij} a^{l-1}_j + b^l_i
\end{aligned}
\tag{b1}\label{b1}
$$

The $a^l_i$ is the output of $l$th layer's $i$th neuron and the $z^l_i$ is its input.

In the training of network, how to calculate the gradient of $W$ and $b$ is difficult problem. One of the solutions called back propagation algorithm, which consider the error of each neuron:

$$\Delta^l_i = \frac{\partial C}{\partial z^l_i}\tag{b2}\label{b2}$$

where $C$ is the cost function:

$$C = \frac{1}{n}\sum_{x} f(y_i, a^L_i(x))$$

where $f$ is a measure of distance between real value and prediction, $n$ is the sample size.

For $L$th layer,

$$\Delta^L_i = \frac{\partial C}{\partial z^L_i} = \frac{\partial C}{\partial a^L_j} \frac{\partial a^L_j}{\partial a^L_i} = \frac{\partial C}{\partial a^L_j} \delta_{ji}\sigma(z^L_j) = \frac{\partial C}{\partial a^L_i}\sigma(z^L_i)\tag{1}\label{1}$$

Notice, the indices in function make no sense in Einstein summation convention. For $l \leq L$,

$$
\begin{aligned}
\Delta^L_i =& \frac{\partial C}{\partial z^l_i} = \frac{\partial C}{\partial z^{l+1}_k}\frac{\partial z^{l+1}_k}{\partial a^l_j} \frac{\partial a^l_j}{\partial z^l_i}\\
=& \Delta^{l+1}_k W^l_{kj} \delta_{ji} \sigma(z^l_j) = \Delta^{l+1}_k W^l_{ki} \sigma(z^l_i)
\end{aligned}
\tag{2}\label{2}
$$

Form the equation $\eqref{b1}$, $\eqref{b2}$, we infer

$$
\begin{aligned}
\frac{\partial C}{\partial W^l_{ij}} =& \frac{\partial C}{\partial z^l_k} \frac{\partial z^l_k}{\partial W^l_{ij}} = \Delta^l_k \delta_{ki} a^{l-1}_j = \Delta^l_i a^{l-1}_j \\
\frac{\partial C}{\partial b^l_i} =& \frac{\partial C}{\partial z^l_j} \frac{\partial z^l_j}{\partial b^l_i} = \Delta^l_j \delta_{ji} = \Delta^l_i
\end{aligned}
\tag{3}\label{3}
$$

With the four equation $\eqref{1}$, $\eqref{2}$, $\eqref{3}$, we can calculate the gradient of $W$ and $b$. In the equation $\eqref{3}$, we can see the degree of freedom is overrated. This is why the back propagation algorithm is a fast algorithm.
