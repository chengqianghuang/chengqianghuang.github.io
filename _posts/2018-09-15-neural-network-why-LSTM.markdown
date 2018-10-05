---
layout: post
title:  "Neural Network - Why LSTM Works?"
date:   2018-09-15 10:11:14 +00:00
categories: neural network
---
In this post, I am trying to understand the reason why LSTM can deal with vanishing and exploding gradient so that it is better than normal RNN in modeling long-term dependencies in sequential data. To start with, we have to comprehend what are vanishing and exploding gradient. Paper [1] is a really good reference to this.

Basically, back propagation is the fundamental method used to train a neural network. In recurrent neural networks (or deep neural networks), due to the reason that the gradient has to propagate back multiple time step, it is running the risk that the gradient will reduce to 0 or explode to a huge number.


1.Vanishing and Exploding Gradient
======
<img src="../../../../../../img/blog/lstm-gradient-problem.png" width="600" height="350"/>

More formally, as shown in Fig.2 (cited from [1]), to perform gradient descent, one has to compute the gradients for the parameters inside the hidden unit. Due to the reason that  the hidden unit is shared along all the time steps, the gradients for the parameters inside the hidden unit could be concluded as:

<a href="https://www.codecogs.com/eqnedit.php?latex=\frac{\partial&space;\varepsilon}{\partial&space;\theta}&space;=&space;\sum_{1\leq&space;t\leq&space;T}&space;\frac{\partial&space;\varepsilon_t}{\partial&space;\theta}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;\varepsilon}{\partial&space;\theta}&space;=&space;\sum_{1\leq&space;t\leq&space;T}&space;\frac{\partial&space;\varepsilon_t}{\partial&space;\theta}" title="\frac{\partial \varepsilon}{\partial \theta} = \sum_{1\leq t\leq T} \frac{\partial \varepsilon_t}{\partial \theta}" /></a>,

where <a href="https://www.codecogs.com/eqnedit.php?latex=\varepsilon_t" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\varepsilon_t" title="\varepsilon_t" /></a> is the error measure (loss) in time <a href="https://www.codecogs.com/eqnedit.php?latex=t" target="_blank"><img src="https://latex.codecogs.com/gif.latex?t" title="t" /></a>, and <a href="https://www.codecogs.com/eqnedit.php?latex=\varepsilon" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\varepsilon" title="\varepsilon" /></a> is the group of all error measures from time 1 to <a href="https://www.codecogs.com/eqnedit.php?latex=t" target="_blank"><img src="https://latex.codecogs.com/gif.latex?t" title="t" /></a>.
While, <a href="https://www.codecogs.com/eqnedit.php?latex=\theta" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\theta" title="\theta" /></a> is the vector of parameters in the shared hidden unit. Thus, the formula above aggregates the information given by all the error measures in each time step to identify the overall gradient for updating the parameters. Afterward, for each time step, the partial derivative could be further decomposed as:

<a href="https://www.codecogs.com/eqnedit.php?latex=\frac{\partial&space;\varepsilon_t}{\partial&space;\theta}&space;=&space;\sum_{1\leq&space;k&space;\leq&space;t}&space;\Big(&space;\frac{\partial&space;\varepsilon_t}{\partial&space;x_t}\frac{\partial&space;x_t}{\partial&space;x_k}\frac{\partial&space;x_k}{\partial&space;\theta}&space;\Big)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;\varepsilon_t}{\partial&space;\theta}&space;=&space;\sum_{1\leq&space;k&space;\leq&space;t}&space;\Big(&space;\frac{\partial&space;\varepsilon_t}{\partial&space;x_t}\frac{\partial&space;x_t}{\partial&space;x_k}\frac{\partial&space;x_k}{\partial&space;\theta}&space;\Big)" title="\frac{\partial \varepsilon_t}{\partial \theta} = \sum_{1\leq k \leq t} \Big( \frac{\partial \varepsilon_t}{\partial x_t}\frac{\partial x_t}{\partial x_k}\frac{\partial x_k}{\partial \theta} \Big)" /></a>.

Furthermore, we can find that:

<a href="https://www.codecogs.com/eqnedit.php?latex=\frac{\partial&space;x_t}{\partial&space;x_k}&space;=&space;\prod_{k&space;<&space;i&space;\leq&space;t}&space;\frac{\partial&space;x_i}{\partial&space;x_{i-1}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;x_t}{\partial&space;x_k}&space;=&space;\prod_{k&space;<&space;i&space;\leq&space;t}&space;\frac{\partial&space;x_i}{\partial&space;x_{i-1}}" title="\frac{\partial x_t}{\partial x_k} = \prod_{k < i \leq t} \frac{\partial x_i}{\partial x_{i-1}}" /></a>.

Then here comes the question. When <a href="https://www.codecogs.com/eqnedit.php?latex=\frac{\partial&space;x_i}{\partial&space;x_{i-1}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;x_i}{\partial&space;x_{i-1}}" title="\frac{\partial x_i}{\partial x_{i-1}}" /></a> is always smaller than a constant <a href="https://www.codecogs.com/eqnedit.php?latex=\eta&space;<&space;1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\eta&space;<&space;1" title="\eta < 1" /></a>, it has the product of gradients **goes to 0 exponentially fast** with <a href="https://www.codecogs.com/eqnedit.php?latex=t&space;-&space;k" target="_blank"><img src="https://latex.codecogs.com/gif.latex?t&space;-&space;k" title="t - k" /></a>:

<a href="https://www.codecogs.com/eqnedit.php?latex=\frac{\partial&space;x_t}{\partial&space;x_k}&space;=&space;\prod_{k&space;<&space;i&space;\leq&space;t}&space;\frac{\partial&space;x_i}{\partial&space;x_{i-1}}&space;\leq&space;\eta^{t-k}&space;<&space;1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;x_t}{\partial&space;x_k}&space;=&space;\prod_{k&space;<&space;i&space;\leq&space;t}&space;\frac{\partial&space;x_i}{\partial&space;x_{i-1}}&space;\leq&space;\eta^{t-k}&space;<&space;1" title="\frac{\partial x_t}{\partial x_k} = \prod_{k < i \leq t} \frac{\partial x_i}{\partial x_{i-1}} \leq \eta^{t-k} < 1" /></a>.

Similarly, if the value of the derivative is always greater than 1 or bigger, it is running the risk of gradient explosion, i.e., **the gradient increases exponentially**. Note that we are using one-dimensional case here to illustrate the problem. Please refer to [1] for multi-dimensional case.


2.Why LSTM Works?
======
It is now clear that the key to ease the issue of vanishing and exploding gradient is to carefully manipulate the partial derivative <a href="https://www.codecogs.com/eqnedit.php?latex=\frac{\partial&space;x_i}{\partial&space;x_{i-1}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;x_i}{\partial&space;x_{i-1}}" title="\frac{\partial x_i}{\partial x_{i-1}}" /></a> to maintain a reasonable value of the overall gradient <a href="https://www.codecogs.com/eqnedit.php?latex=\frac{\partial&space;\varepsilon}{\partial&space;\theta}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;\varepsilon}{\partial&space;\theta}" title="\frac{\partial \varepsilon}{\partial \theta}" /></a>.

<img src="../../../../../../img/blog/lstm-chain.png" width="700" height="275"/>

In the figure above (quoted from [Colah's blog][b1]), it shows the inner structure of a LSTM unit. The input/output is composed of two parts: a context state and a hidden state (shown below, quoted from [Colah's blog][b1]). Sorry for the abuse of notation <a href="https://www.codecogs.com/eqnedit.php?latex=x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x" title="x" /></a> here. In the figures, <a href="https://www.codecogs.com/eqnedit.php?latex=x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x" title="x" /></a> is the input for a LSTM unit, while in the previous section, we use <a href="https://www.codecogs.com/eqnedit.php?latex=x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x" title="x" /></a> as the hidden state in a RNN cell.

<img src="../../../../../../img/blog/lstm-context.png" width="700" height="250"/>
<img src="../../../../../../img/blog/lstm-hidden.png" width="700" height="250"/>

It can be derived from previous section that <a href="https://www.codecogs.com/eqnedit.php?latex=\frac{\partial&space;h_t}{\partial&space;h_{t-k}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;h_t}{\partial&space;h_{t-k}}" title="\frac{\partial h_t}{\partial h_{t-k}}" /></a> is still the product of a series of derivatives. We could put it more formally and derive that:

<a href="https://www.codecogs.com/eqnedit.php?latex=\frac{\partial&space;h_t}{\partial&space;h_{t-k}}&space;=&space;\prod_{1&space;<&space;i&space;\leq&space;t}&space;\frac{\partial&space;h_i}{\partial&space;h_{i-1}}&space;=&space;\prod_{1&space;<&space;i&space;\leq&space;t}&space;\Big(\frac{\partial&space;h_i}{\partial&space;C_i}\frac{\partial&space;C_i}{\partial&space;h_{i-1}}&space;&plus;&space;\frac{\partial&space;h_i}{\partial&space;o_i}\frac{\partial&space;o_i}{\partial&space;h_{i-1}}&space;\Big)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;h_t}{\partial&space;h_{t-k}}&space;=&space;\prod_{1&space;<&space;i&space;\leq&space;t}&space;\frac{\partial&space;h_i}{\partial&space;h_{i-1}}&space;=&space;\prod_{1&space;<&space;i&space;\leq&space;t}&space;\Big(\frac{\partial&space;h_i}{\partial&space;C_i}\frac{\partial&space;C_i}{\partial&space;h_{i-1}}&space;&plus;&space;\frac{\partial&space;h_i}{\partial&space;o_i}\frac{\partial&space;o_i}{\partial&space;h_{i-1}}&space;\Big)" title="\frac{\partial h_t}{\partial h_{t-k}} = \prod_{1 < i \leq t} \frac{\partial h_i}{\partial h_{i-1}} = \prod_{1 < i \leq t} \Big(\frac{\partial h_i}{\partial C_i}\frac{\partial C_i}{\partial h_{i-1}} + \frac{\partial h_i}{\partial o_i}\frac{\partial o_i}{\partial h_{i-1}} \Big)" /></a>.

This is due to the reason that in each LSTM cell, there are two paths that <a href="https://www.codecogs.com/eqnedit.php?latex=h_{i-1}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?h_{i-1}" title="h_{i-1}" /></a> could affect <a href="https://www.codecogs.com/eqnedit.php?latex=h_{i}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?h_{i}" title="h_{i}" /></a>.

More importantly, it is noticed that, after solving the product, we could find an item:

<a href="https://www.codecogs.com/eqnedit.php?latex=\frac{\partial&space;h_t}{\partial&space;C_t}\frac{\partial&space;C_t}{\partial&space;h_{t-1}}\frac{\partial&space;h_{t-1}}{\partial&space;C_{t-1}}\frac{\partial&space;C_{t-1}}{\partial&space;h_{t-2}}&space;\cdots&space;\frac{\partial&space;h_{t-k&plus;1}}{\partial&space;C_{t-k&plus;1}}\frac{\partial&space;C_{t-k&plus;1}}{\partial&space;h_{t-k}}&space;=&space;\frac{\partial&space;h_t}{\partial&space;C_t}\frac{\partial&space;C_t}{\partial&space;C_{t-1}}&space;\cdots&space;\frac{\partial&space;C_{t-k&plus;2}}{\partial&space;C_{t-k&plus;1}}\frac{\partial&space;C_{t-k&plus;1}}{\partial&space;h_{t-k}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;h_t}{\partial&space;C_t}\frac{\partial&space;C_t}{\partial&space;h_{t-1}}\frac{\partial&space;h_{t-1}}{\partial&space;C_{t-1}}\frac{\partial&space;C_{t-1}}{\partial&space;h_{t-2}}&space;\cdots&space;\frac{\partial&space;h_{t-k&plus;1}}{\partial&space;C_{t-k&plus;1}}\frac{\partial&space;C_{t-k&plus;1}}{\partial&space;h_{t-k}}&space;=&space;\frac{\partial&space;h_t}{\partial&space;C_t}\frac{\partial&space;C_t}{\partial&space;C_{t-1}}&space;\cdots&space;\frac{\partial&space;C_{t-k&plus;2}}{\partial&space;C_{t-k&plus;1}}\frac{\partial&space;C_{t-k&plus;1}}{\partial&space;h_{t-k}}" title="\frac{\partial h_t}{\partial C_t}\frac{\partial C_t}{\partial h_{t-1}}\frac{\partial h_{t-1}}{\partial C_{t-1}}\frac{\partial C_{t-1}}{\partial h_{t-2}} \cdots \frac{\partial h_{t-k+1}}{\partial C_{t-k+1}}\frac{\partial C_{t-k+1}}{\partial h_{t-k}} = \frac{\partial h_t}{\partial C_t}\frac{\partial C_t}{\partial C_{t-1}} \cdots \frac{\partial C_{t-k+2}}{\partial C_{t-k+1}}\frac{\partial C_{t-k+1}}{\partial h_{t-k}}" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex==&space;\frac{\partial&space;h_t}{\partial&space;C_t}&space;\frac{\partial&space;C_{t-k&plus;1}}{\partial&space;h_{t-k}}&space;\prod_{0<i\leq&space;k-2}&space;\frac{\partial&space;C_{t-i}}{\partial&space;C_{t-i-1}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?=&space;\frac{\partial&space;h_t}{\partial&space;C_t}&space;\frac{\partial&space;C_{t-k&plus;1}}{\partial&space;h_{t-k}}&space;\prod_{0<i\leq&space;k-2}&space;\frac{\partial&space;C_{t-i}}{\partial&space;C_{t-i-1}}" title="= \frac{\partial h_t}{\partial C_t} \frac{\partial C_{t-k+1}}{\partial h_{t-k}} \prod_{0<i\leq k-2} \frac{\partial C_{t-i}}{\partial C_{t-i-1}}" /></a>,

in which the product can be further analysed as (notations could be found in following figure, quoted from [Colah's blog][b1]):

<a href="https://www.codecogs.com/eqnedit.php?latex=\prod_{0<i\leq&space;k-2}&space;\frac{\partial&space;C_{t-i}}{\partial&space;C_{t-i-1}}&space;=&space;\prod_{t-k&plus;2&space;<&space;i&space;<&space;t}&space;f_i&space;=&space;\prod_{t-k&plus;2&space;<&space;i&space;<&space;t}&space;\sigma&space;(W_i[h_{i-1},&space;x_i]&plus;b_i)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\prod_{0<i\leq&space;k-2}&space;\frac{\partial&space;C_{t-i}}{\partial&space;C_{t-i-1}}&space;=&space;\prod_{t-k&plus;2&space;<&space;i&space;<&space;t}&space;f_i&space;=&space;\prod_{t-k&plus;2&space;<&space;i&space;<&space;t}&space;\sigma&space;(W_i[h_{i-1},&space;x_i]&plus;b_i)" title="\prod_{0<i\leq k-2} \frac{\partial C_{t-i}}{\partial C_{t-i-1}} = \prod_{t-k+2 < i < t} f_i = \prod_{t-k+2 < i < t} \sigma (W_i[h_{i-1}, x_i]+b_i)" /></a>

It is discussed in thesis [2] (page 14) that the quantity of this product is safe from vanishing and exploding. Therefore, we are **optimistic** that the overall gradient, i.e., <a href="https://www.codecogs.com/eqnedit.php?latex=\frac{\partial&space;\varepsilon&space;}{\partial&space;\theta}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;\varepsilon&space;}{\partial&space;\theta}" title="\frac{\partial \varepsilon }{\partial \theta}" /></a>, will not be too small or too big so that same from vanishing and exploding gradient.
Note here again that:

<a href="https://www.codecogs.com/eqnedit.php?latex=\frac{\partial&space;\varepsilon&space;}{\partial&space;\theta}&space;=&space;\sum_{1\leq&space;t&space;\leq&space;T}&space;\frac{\partial&space;\varepsilon_t}{\partial&space;\theta}&space;=&space;\sum_{1\leq&space;t&space;\leq&space;T}\sum_{1\leq&space;k&space;\leq&space;t}&space;\frac{\partial&space;\varepsilon_t}{\partial&space;h_t}\frac{\partial&space;h_t}{\partial&space;h_{t-k}}\frac{\partial&space;h_{t-k}}{\partial&space;\theta}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;\varepsilon&space;}{\partial&space;\theta}&space;=&space;\sum_{1\leq&space;t&space;\leq&space;T}&space;\frac{\partial&space;\varepsilon_t}{\partial&space;\theta}&space;=&space;\sum_{1\leq&space;t&space;\leq&space;T}\sum_{1\leq&space;k&space;\leq&space;t}&space;\frac{\partial&space;\varepsilon_t}{\partial&space;h_t}\frac{\partial&space;h_t}{\partial&space;h_{t-k}}\frac{\partial&space;h_{t-k}}{\partial&space;\theta}" title="\frac{\partial \varepsilon }{\partial \theta} = \sum_{1\leq t \leq T} \frac{\partial \varepsilon_t}{\partial \theta} = \sum_{1\leq t \leq T}\sum_{1\leq k \leq t} \frac{\partial \varepsilon_t}{\partial h_t}\frac{\partial h_t}{\partial h_{t-k}}\frac{\partial h_{t-k}}{\partial \theta}" /></a>.

<img src="../../../../../../img/blog/lstm-ft.png" width="700" height="250"/>


3.Discussion
======
To be honest, I am not fully convinced by the aforementioned derivation. The key product can certainly approach 0 in specifica cases, although it will not explode. Hence, I am still waiting for better explanation. Practical experiments have shown that LSTM can be trained but it still has limitations in extracting long-term patterns/dependencies of sequential data. Certain research has tried to supersede the utilisation of RNN with other mechanism, e.g., [Attention is all you need][a1]. Maybe, I mean maybe, RNN is not really necessary?

4.References
======
[1] Razvan Pascanu, Tomas Mikolov, Yoshua Bengio, *On the difficulty of training recurrent neural networks*, ICML, vol. 3, no. 28, pp. 1310-1318, 2013.

[2] Justin Simon Bayer, *Learning Sequence Representations*, Dissertation, Technische Universität München, 2015.

[3] [quora.com question][c1]

[4] [stackexchange.com question][c2]

[a1]: https://arxiv.org/abs/1706.03762
[b1]: http://colah.github.io/posts/2015-08-Understanding-LSTMs/
[c1]: https://www.quora.com/How-does-LSTM-help-prevent-the-vanishing-and-exploding-gradient-problem-in-a-recurrent-neural-network
[c2]: https://stats.stackexchange.com/questions/185639/how-does-lstm-prevent-the-vanishing-gradient-problem