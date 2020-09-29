# Deep Reinforcement Continuous Control Report

## Learning Algorithm <a name="algorithm"></a>
The algorithm used is based on the DDPG Actor Critic Model. It is wrapped arount a classic 
Multi Agent structure to share the Replay Memory buffer between the two agents. Start point for the code was the algorithm used in p2.

Further information regarding the design can be found in the paper _Multi-Agent-Critic for Mixed Cooperative Environments_ 
(Source: https://papers.nips.cc/paper/7217-multi-agent-actor-critic-for-mixed-cooperative-competitive-environments.pdf).

The model itself consists of two neural networks: Actor- and Critic-model. The Actor-model estimates the policy. It takes as input the current state
to output the action to take at this step. The Critic-model is used for value estimation, to maximize the value from the input state.

Both Actor and Critic have a local and a target model. The target models are a copy from the local models after each iteration to slowly track the local models.

Like other reinforcement learning models, DDPG uses a replay buffer to sample experience tuples to update the neural networks at each iteration. 
Random batches of state-action-reward-action' tuples are sampled to update and take an action.

The models have the following architecture:

| Actor Model Layer  | Shape |
| ------------- | ------------- |
| Input Layer | _24_ x 128  |
| BatchNorm Layer  | 128  |
| Dense Hidden Layer  | 128 x 64  |
| Output Layer  | 64 x _2_  |

| Critic Model Layer  | Shape |
| ------------- | ------------- |
| Input Layer | _24_ x 128  |
| BatchNorm Layer  | 128  |
| Dense Hidden Layer  | 130 x 64  |
| Output Layer  | 0.2  |
| Output Layer  | 64 x _2_  |

Here the ionput is the number of states _24_, and the output is the actions possible for the agent _2_.

The agent was trained with the following Hyperparameters:

| Hyperparameter  | Value |
| ------------- | ------------- |
| Replay Buffer Size | 1e5  |
| Minibatch Size  | 128  |
| Discount Rate  | 0.99  |
| TAU  | 1e-3  |
| Actor Learning Rate | 1e-4  |
| Critic Learning Rate | 1e-4  |
| L2 Weight Decay | 1e-6  |

## Plot of Rewards <a name="plot"></a>

![Solved Agent][graph.png]

The goal of this project was to reach an average reward of over 0.5 from at least 100 episodes of either agent.
After training the agent with different configuration/hyperparameters, the best options are shown in the hyperparameter table.
A learning rate of `1e-4` was best.

Using the current configuration, the target average was reached approximately after **2,000 episodes **. 
Nevertheless the model was trained 5000 episodes and the best model was used.

## Future Ideas (#futureideas)

Options to improve the results:
- Further hyperparameter tuning

- Extending architecture (i.e. adding additional hidden layers)

- Add a prioritized replayer, which improves the sample selection from the replay buffer.

- Using other algroithms (i.e. TD3)

- Changing environment (i.e. Soccer-Agent)
