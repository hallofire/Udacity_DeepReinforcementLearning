# Project 2: Continuous Control - Report

### Introduction

This report describes my approach to solve the project "p2_continuous-control".
I choose to solve Version 1, because I am a new comer to rl and it seemed more appropriate
In order to solve the challenge I used my collected knowledge, the paper "Continuous Control with Deep Learning"
by Lilicrap, Philip etc. and internet research.
This attempt is my second architecture to solve the problem. I streamlined my first code and made changes.


### Hyperparameters

I used the classic hyperparameters to solve the environment
- Replay Buffer Size = 1e6
- Mini Batch Size = 128
- TAU (for soft-updaze of the target parameters) = 1e-3
- Learning Rate Actor = 1e-4
- Learning Rate Critic = 1e-4
- Noise = Ornstein-Uhlenbeck
- Discount Factor = 0.99

### Actor Model

The network has a two hidden layers 128 x 128 and uses batch normalization after the first and the second hidden layer.

### Critic Model

The network has a two hidden layers 128 x 128 and uses batch normalization after the first and the second hidden layer.

#### Results

The environment was solved in over 300 episodes. 
Analyzing the given graph we see that first the learning starts quite linearly. But after approximately 120 episodes we get a rising fluctuation between the single episodes.
The aimed goal of series of 30 was reached after XXX episodes. 

#### Further Improvements

1) Tune the hyperparameters to reach a higher reward even faster
2) Using prioritized replay buffer
3) Adjusting the rewards (i.e. negative rewards for discouraging the agent)
4) Solving V2 of the project