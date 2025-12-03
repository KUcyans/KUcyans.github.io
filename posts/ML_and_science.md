---
layout: post
title: Machine Learning and Science
date: 2025-11-02
permalink: /posts/ml_science/
cover: /assets/img/val_loss.png
---

# What is Machine Learning in Scientific Context?

<!-- key: ML, model, algorithm, parameters, training, loss function,  -->

Machine learning (ML) can be viewed as a method for finding optimal solutions to complex problems. It has attracted increasing attention from scientists who work with multivariate, high-dimensional data. In ML, we specify a mathematical function with parameters, organised according to a particular structure called an architecture. Given a dataset, the learning algorithm evaluates many combinations of these parameters. By measuring how well the function performs by monitoring a quantity known as the loss, the algorithm adjusts the parameters in order to reduce this loss. Training of a model referes to iteration of this process. Training ultimately produces a specific set of parameters associated with a chosen architecture, and this combination is what we call a model. A model is thought to generalise the patterns in the data well, so that one can generate a solution for a different data set.


# Training a Model
<!-- key: supervised learning?, overfitting, training, split, validation, loss, test, prediction/inference -->
Broadly speaking, ML has two approaches: supervised learning and unsupervised learning.
1. Supervised learning: the model learns from labelled examples with known outcomes
2. Unsupervised learning: the model discovers patterns without labels  
Both are widely used in various fields in science, but in this post, we will focus on supervised learning comparing predictions with known targets.

In supervised learning, we must ensure that the model does not simply memorise the training data but instead generalise patterns. Then, how can we ensure the model is generalising the pattern in data properly?

During training, the loss on the training dataset usually decreases as the model becomes better at fitting the examples it sees. ¡Warning! There is a pitfall ahead: a model may become very good at reproducing the training examples while failing to generalise to new, unseen data. This phenomenon is known as overfitting.


![Training and Validation losses](/assets/img/val_loss.png){: width="75%" }  

 **Figure 1**: Typical shape of training and validation loss. The point where the validation loss hit the bottom is considered the best model!

To detect this, we split the available data into separate subsets. One subset is used exclusively for training and is called the training dataset. At the end of each training epoch, we evaluate the same loss function on a second subset that the model has not seen during training. We call the second dataset thus the validation dataset. When the validation loss begins to rise even as the training loss continues to fall, it tells that the model is focusing to much on the training data's specific patterns rather than generalising well.

A third subset, kept entirely unseen until all training decisions are finished, is called the test dataset. This final dataset provides an unbiased estimate of the model’s true performance on new data.

# ML in Science: just another kind of fitting method
But doesn't that sound familiar? Isn't it like Chi² fitting? Yes! it is. Fundamentally, supervised learning is just like Chi² or maximum likelyhood fitting, trying different parameters and find the most optimal parameter combination. 


We have learned 

- Start by showing data: linear
- Try to fit it: how would you do? draw a line/curve? 
- Chi square fit: minimisation of chi square sum: trivial, evident logic
- What about this data?
- Even more complex data? Surely we can use a similar method for multidimensional setup, bu are you really going to test all the functions you know that look like fitting to the data distribution? How would you fit multivariate complex problems?
  - How would you find the optimal route on a map where roads may not be linear
  - How would you simulate the evolution of cells 
  - How would you tell what particle was that in a given event from gigantic particle detectors where they may generate more than one petabyte of data per second
  - think about other examples where ML is already irreplaceable
- The idea of using ML is to build a model that is capable of capturing complex pattern under the hood
- Now, the model is...
  - not expressed in analytic parameters as in coefficients or exponents of an equation
  - expressed in numerical parameters which are structured in some structure/shape called a model
  - together with the values of parameters and the structure they are memoriesed plays a role as a 'fit' as the linear function we first saw
  - So they are not comprehensible by being visually investigated
  - Yet we can understand what is the governing logic of the building blocks and the structures of the models
