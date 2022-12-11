---
layout: post
title:  "Batch Normalization"
date:   2018-05-23 11:51:11
categories: blog
---
We normalize the input layer , For example if we got some features from 0 to 1 and some from 1 to 1000 , we normalize them to speed up learning. If input is getting benefit then we should do it for the values in hidden layers , they usually change all the times and get 10 times or more improvement in training speed.

BN reduces the amount by what the hidden unit values shift around (covariance shift). 

Next question : What's covariance shift ? 
Suppose we train our network on black cat images. If we apply it to data of colored cats then it will not work as expected. In other words, if an algorithm learned some X to Y mapping, and if the distribution of X changes, then we might need to retrain the learning algorithm by trying to align the distribution of X with the distribution of Y.

Batch normalization allows each layer of a network to learn by itself more independently of other layers.

Higher learning rates are can be used because of batch normalization as there's no activation that went very high or very low. Things that didn't train earlier will start to train.

It reduces overfitting because it has a slight regularization effects. Similar to dropout, it adds some noise to each hidden layer’s activations. Therefore, if we use batch normalization, we will use less dropout, which is a good thing because we are not going to lose a lot of information. However, we should not depend only on batch normalization for regularization; "we should better use it together with dropout".

WORKING :

BN normalizes the output of activation layer by subtracting the batch mean and dividing by batch standard deviation.

However, after this shift/scale of activation outputs by some randomly initialized parameters, the weights in the next layer are no longer optimal. SGD ( Stochastic gradient descent) undoes this normalization if it’s a way for it to minimize the loss function.

 In other words, batch normalization lets SGD (Stochastic gradient descent) do the denormalization by changing only these two weights for each activation, instead of losing the stability of the network by changing all the weights.
 
use of momentum in BN is

running_mean[t] = running_mean[t-1]*0.9 + batch_mean[t]*0.1

this 0.1 here is nothing but momentum
(The running mean and variances are computed using an exponential moving average with smoothing factor 0.1)
