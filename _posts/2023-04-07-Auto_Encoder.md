---
title: Auto Encoder
author: SeHoon
date: 2023-04-07 14:24:30 +0900
categories: [Deep Learning, DL_Introduction]
tags: [deep learning, python]
math: true
mermaid: true
---


# What is Auto Encoder?
Auto encoder is an unsupervised deep learning that is used for:
+ Feature detections.<br>
When auto encoder encodes datas, the hidden layer represents important features. And we can use the features.
+ Recommendation system.<br>
+ Encoding.<br>

Auto encoder encodes itself. So, auto encoder takes some inputs, put it to the hidden layer, and then gets the outputs with the same number as the inputs.<br>

Here is a simple structure of auto encoder:
<center>
<img src="https://user-images.githubusercontent.com/28240052/232176425-4140165a-ac3e-4d9c-8357-795a847c33a0.png" width=400>
</center>
<br>

Auto encoder is directed types of neural network unlike [boltzmann machine](https://csh970605.github.io/posts/Boltzmann_Machine/).<br>
<br>

# How does Auto Encoder works?
Here is a simplified auto encoder:
<center>
<img src="https://user-images.githubusercontent.com/28240052/232210406-0781ef41-ce2a-4cd7-9cbb-edf5f99ea38f.png" width=600>
</center>
<br><br>

We are going to encode the ratings of movies that people have rated. "1" means they liked the movie and "0" means they didn't like the movie.<br>
And then, as an example, set the weights like:
<center>
<img src="https://user-images.githubusercontent.com/28240052/232227829-684dd24f-1111-4a5a-a078-ebc5d4588ff9.png" width=600>
</center>
<br><br>
Though we set the weights like in the image above as an example, in auto encoder, hyperbolic tangent usually used to set weights.<br>
<br><br>
And we get input "[1 0 0 0]".
<center>
<img src="https://user-images.githubusercontent.com/28240052/232228496-1b3ad1b5-232e-4965-9781-207dade786b0.png" width=600>
</center>
<br><br>
Computing the input with the weights gives the output "[2 0 0 -2]".
<center>
<img src="https://user-images.githubusercontent.com/28240052/232228547-8720f456-0d2d-470a-a837-6717dcb71455.png" width=600>
</center>
<br><br>

But, this is not the end. By using [softmax function](https://csh970605.github.io/posts/Softmax/), the output is "[1 0 0 0]"

<center>
<img src="https://user-images.githubusercontent.com/28240052/232228892-b8512a68-c66b-418f-b5ad-9ceca9cf8766.png" width=200>
</center>
<br><br>

In this case, the input is the same as the output.<br>
Then, how the output isn't the same as the input? It is easily solved by adding biases.
<center>
<img src="https://user-images.githubusercontent.com/28240052/232277193-cc8c0476-bf4d-4861-a8ab-0e147c67a6e5.png" width=600>
</center>
<br><br>




# Training steps of an Auto Encoder
Let's see the steps of training by example.<br>
As an example, we have movie ratings from various users.
<center>
<img src="https://user-images.githubusercontent.com/28240052/232277621-887eb48e-426c-4d69-908c-74e7e6519e6d.png" width=400>
</center>
<br><br>

+ STEP 1 <br>
We start with an array where the lines (the observations) correspond to the users and the columns (the features) correspond to the movies. Each cell (u, i) contains the rating (from 1 to 5, 0 if no rating) of the movie i by the user u.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/232277621-887eb48e-426c-4d69-908c-74e7e6519e6d.png" width=400>
</center>
<br><br>

+ STEP 2<br>
The first user goes into the network. The input vector $x = (r_{1}, r_{2}, ..., r_{m})$ contains all its ratings for all the movies.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/232278246-fe14b895-d7a3-4197-9cf2-53c9124082ae.png" width=400>
</center>
<br><br>

+ STEP 3<br>
The input vector x is encoded into a vector z of lower dimensions by a mapping function f (e.g: sigmoid function):<br>
<center>

$z = f(Wx + b)$ where W is the vector of input weights and b the bias<br>
<img src="https://user-images.githubusercontent.com/28240052/232278325-c40ab3b5-5a83-4e0d-ac6b-2884d8e9b6b0.png" width=400>
</center>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Although there is randomly initialized weights, encoding is performed.<br><br>

+ STEP 4<br>
z is then decoded into the output vector y of same dimensions as x, aiming to replicate the input vector x.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/232278692-0dc50996-4363-4eac-81ab-ea3f00d02b2f.png" width=500>
</center>
<br><br>

+ STEP 5<br>
The reconstruction error d(x, y) = $||x\ -\ y||$ is computed. The goal is to minimize it.<br>
+ STEP 6<br>
Back-Propagation: from right to left, the error is back-propagated. The weights are updated according to how much they are responsible for the error. The learning rate decides by how much we update the weights.<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/232278758-0fc32bbc-090d-44a0-9eb4-4b3ed6c44608.png" width=400>
</center>
<br><br>

+ STEP 7<br>
Repeat Steps 1 to 6 and update the weights after each observation (Reinforcement Learning).<br>
Or Repeat Steps 1 to 6 but update the weights only after a batch of observations (Batch Learning). <br>

+ STEP 8<br>
When the whole training set passed through the ANN, that makes an epoch. Redo more epochs.<br>
<br><br><br>

# Overcomplete Hidden Layers
Overcomplete hidden layers are used for lots of variations of autoencoders. For example, we want to get more hidden nodes than input layer to use autoencoder as a feature extractor to get more features, we can use overcomplete hidden layers.<br>
But there is a problem. If there are more hidden layers than input layer, autoencoder can use a cheat like "values in boxes of the same color are always the same."<br>
<center>
<img src="https://user-images.githubusercontent.com/28240052/232283557-728c8877-d286-4ddb-ab7b-cca8a103c9b8.png" width=400>
</center>
<br><br>

In this way, we can't extract any valuable features from autoencoder. To solve this problem, there are several different types of autoencoders and I'll introduce it below.
<br><br><br>

# Types of Auto Encoders

+ [Sparse Autoencoder](https://csh970605.github.io/posts/Sparse_Autoencoder/)<br>

+ [Denoising Autoencoder](https://csh970605.github.io/posts/Denoising_Autoencoder/)<br>

+ [Contractive Autoencoder](https://csh970605.github.io/posts/Contractive_Autoencoder/)<br>

+ [Stacked Autoencoder](https://csh970605.github.io/posts/Stacked_Autoencoder/)<br>

+ [Deep Autoencoder](https://csh970605.github.io/posts/Deep_Autoencoder/)<br>


<br><br>

# Example
<br><br>

## Code

```py
import numpy as np
import pandas as pd
import torch
import torch.nn as nn
import torch.nn.parallel
import torch.optim as optim
import torch.utils.data
from torch.autograd import Variable

# Importing the data
movies = pd.read_csv('ml-1m/movies.dat', sep='::', header=None, engine='python', encoding='latin-1')
users = pd.read_csv('ml-1m/users.dat', sep='::', header=None, engine='python')
ratings = pd.read_csv('ml-1m/ratings.dat', sep='::', header=None, engine='python')

# Preparing the training set and the test set
training_set = pd.read_csv('ml-100k/u1.base', delimiter='\t', )
training_set = np.array(training_set, dtype='int')
test_set = pd.read_csv('ml-100k/u1.test', delimiter='\t', )
test_set = np.array(test_set, dtype='int')


# Getting the number of users and movies
nb_users = max(max(training_set[:, 0]), max(test_set[:, 0]))
nb_movies = max(max(training_set[:, 1]), max(test_set[:, 1]))

# Converting the data into an array with users in lines and movies in columns
def convert(data):
    new_data = []
    for id_users in range(1, nb_users + 1):
        id_movies = data[:, 1][data[:, 0] == id_users]
        id_ratings = data[:, 2][data[:, 0] == id_users]
        ratings = np.zeros(nb_movies)
        ratings[id_movies - 1] = id_ratings
        new_data.append(list(ratings))
    return new_data
training_set = convert(training_set)
test_set = convert(test_set)

# Converting the data into Torch tensors
training_set = torch.FloatTensor(training_set)
test_set = torch.FloatTensor(test_set)


# Creating the architecture of the Neural Network
class SAE(nn.Module):
    def __init__(self,):
        super(SAE, self).__init__()
        # Full connection connected to autoencoder
        # Linear (input vector, number of hidden neurons)
        self.fc1 = nn.Linear(nb_movies, 20)
        self.fc2 = nn.Linear(20, 10)
        """Since no more encoding layers are added, the number of hidden neurons is configured equal to the number of input vectors at the beginning.
            = decoding"""
        self.fc3 = nn.Linear(10, 20)
        self.fc4 = nn.Linear(20, nb_movies)
        self.activation = nn.Sigmoid()
        
    # Define action in auto encoder
    def forward(self, x):
        x = self.activation(self.fc1(x))
        x = self.activation(self.fc2(x))
        x = self.activation(self.fc3(x))
        x = self.fc4(x)
        return x
    
sae = SAE()
criterion = nn.MSELoss()
optimizer = optim.RMSprop(sae.parameters(), lr=0.01, weight_decay=0.5)

# Training the SAE
epochs = 200
for epoch in range(1, epochs+1):
    train_loss = 0
    s = 0.
    for id_user in range(nb_users):
        input = Variable(training_set[id_user]).unsqueeze(0)
        target = input.clone()
        if torch.sum(target.data > 0) > 0:
            output = sae(input)
            # Calculate descent
            target.require_grad = False
            output[target == 0] = 0
            loss = criterion(output, target)
            # Average the ratings of the rated movies
            mean_corrector = nb_movies/float(torch.sum(target.data > 0) + 1e-10)
            loss.backward()
            train_loss += np.sqrt(loss.data*mean_corrector)
            s += 1.
            optimizer.step()
            """Difference between backward and step
               backward : direction
               step: mass"""
    print('epoch:', epoch, 'loss:', (train_loss/s))
    
# Testing the SAE
test_loss = 0
s = 0.
for id_user in range(nb_users):
    # The reason for leaving the input as training set: Because the items predicted in the training set are in the test set and can be compared together
    input = Variable(training_set[id_user]).unsqueeze(0)
    target = Variable(test_set[id_user]).unsqueeze(0)
    if torch.sum(target.data > 0) > 0:
        output = sae(input)
        target.require_grad = False
        output[target == 0] = 0
        loss = criterion(output, target)
        mean_corrector = nb_movies/float(torch.sum(target.data > 0) + 1e-10)
        loss.backward()
        test_loss += np.sqrt(loss.data*mean_corrector)
        s+=1.
        optimizer.step()
    print('loss:', (test_loss/s))
```
<br><br><br>

## Result


<br><br><br>

# Implementation

+ [Auto Encoder 1](https://github.com/csh970605/Deep_Learning_A-Z/tree/main/Part%206%20-%20AutoEncoders/Section%2019%20-%20AutoEncoders)<br>
+ [Auto Encoder 2](https://github.com/csh970605/TensorFlow-2.0-Advanced/tree/main/Section%203)<br>
+ [Classify autoencoded images by CNN](https://github.com/csh970605/Computer-Vision-Masterclass/tree/main/Section%208)<br>