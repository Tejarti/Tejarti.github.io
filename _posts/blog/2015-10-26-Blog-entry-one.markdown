---
layout: post
title:  "Generative Adversarial Networks"
date:   2018-05-22 16:51:11
categories: blog
---
Traditional Approaches to train neural networks were to simply feed some input values to the network, based on the weights of that network , it will return some output and based on that output , it will calculate some loss if the labels are provided to it.
But back in 2015 Ian Goodefellow proposed a new technique to train these networks, through that approach Mr. Goodfellow generated data by making the network learn the probability distribution function of that data.
Today we will discuss about Generative Adversarial Networks.

Generative adversarial networks consist of two models: a generative (generator) model and a discriminative (discriminator) model :

Task of generator is to generate new images which look similar to the images given in training set. In other words task of generator is to define the correct distribution function such that the when a random noise is passed through this function, it must have the same probability distribution as the original data. In generator we pass a random noise and it gives out the data that makes similar sense as the original data.

The task of discriminator is much similar to the normal classifiers with only difference being that it is trained simultaneously alongside of generator and through partially unsupervised method. A batch of image is passed in discriminator and it has to predict whether the data came from original distribution or from generated data and this is how discriminator is trained.

If i summarize this concept in simple words , generator and discriminator are like two bitter rivals who try to learn from the mistakes of their rivals and try to outrun the other. Neither they can't live with each other nor they can't succeed without each other.

Steps Involved in Training of Gan : 
1) Pre-Processing of images:
For the task of generating new data of RGB images we choose CELEBA dataset to work upon.
First our main task is to pre-process the given images , the main reason behind pre-processing
is to eliminate a lot of extra data behind the face which is not useful, as right now we are
focussing only on face not in background. For this purpose we used the PIL library of python
to open the image and after that cropping only on the face part. When this part is done , we
stored the pixel data inside the numpy array and we returned the array back.

2) Setting up Generator and Discriminator Model:
Here in this step we defined our Generator and Discriminator models on which the data was to
be trained on. In this project we worked on two setups: Sequential and Convolutional.
Model summaries are provided below for both the models. The basic idea of generator model is
to first pass a random noise to first dense layer which will convert and reshape it according to
the neural network defined.
Discriminator model would be used to classify that, input image was from which class i.e. Real
or Generated. (Here Real sample corresponds to Images from CelebA dataset).
Generator model would generate an image back from random noise.

3) Setting up Stacked Model:
The main role of stacked model here is to train Generator Network. The main idea behind
stacked model is that: the input to stack model would be images generated from Generator
network, these images would be passed to Discriminator to check the accuracy that how many
of them belong to real dataset. Here we will set training of discriminator network to false, all
we care about is the weight updation that is brought back by Discriminator.

4) Training Loop:
The main idea here is to first train Discriminator Network, for that purpose we would pass half
batch of real images and half batch of fake images which are generated from generator
network. After the training of Discriminator, it’s time to train Generator network.
To train generator network we will pass a full batch of fake images to stacked up model and on
the basis of that generator network weight updation will take place.
Both our network will fight against each other to surpass each other till the time nash
equilibrium is not established.

<a href="https://github.com/hslog16/GAN">Code is available at this link</a>.
