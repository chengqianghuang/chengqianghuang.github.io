---
layout: post
title:  "Neural Network - Back Propagation"
date:   2018-07-19 14:22:14 +00:00
categories: neural network
---
This post is to help myself understand Neural Networks better, especially the back propagation algorithm. I'll follow the content in [1] to clear all the concepts. If you are reading this, I expect that you have some knowledge about Machine Learning and Optimisation. If not, please refer to [1] for the basics.

Before introducing Neural Networks, the first thing to ask is **why do we need Neural Networks?** Basically, a neural network is a function approximator that takes certain inputs and gives us outputs. Although there are currently various ways of using a neural network, the main purpose of designing a neural network is to identify a function that could fit the observed data well. Compare to other models, Neural Networks are very general and are said to be capable of approximating all kinds of functions.

**Are Neural Networks really that great in approximating functions?** Generally, it is not bad. One could check [Google Neural Network Playground][playground] to see its performance in small datasets. However, for a specific problem, the utilisation of a neural network may not be the best choice. A simplest example would be designing a XOR function, in which case you don't want to use neural network because you could implement XOR with a conditional function. Nevertheless, a neural network can definitely approximate XOR function regardless of the verbose neural network architecture and training process.

**Is a neural network with a single neuron able to approximate an XOR function?** The answer is YES if we allow complex activation functions. Basically, Neural Networks are able to identify non-linear transformations from inputs to outputs with non-linear activation functions. An activation function that complex enough would be able to find us a way to approximate XOR. However, from the standpoint of a general model that are to fit all different types of functions, using a single neuron with complex activation function to achieve function approximation is not a good choice:
* the activation function may be not differentiable, which hinders the training of the Neural Networks;
* the use of a single neuron limits the benefit of automatic feature engineering, i.e, non-linear transformation of data.



<br>

[[1] Andrew Ng, Sparse Autoencoder, CS294A Lecture Notes, 2011.][c1]

[[2] L. Ruff, N. Görnitz, L Deecke, S. A. Siddiqui, R. A. Vandermeulen, A. Binder, E. Muller, M. Kloft, Deep One-Class Classification, ICML, 2018.][c2]

[c1]: https://web.stanford.edu/class/cs294a/sparseAutoencoder_2011new.pdf
[c2]: http://ml.informatik.uni-kl.de/publications/2018/deep-svdd.pdf
[playground]: https://playground.tensorflow.org/