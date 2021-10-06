
## Project 2: Continuous Control

</hr>

### Environment Details

This is a [Unity ML Agent](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) Reacher environment provided by Udacity. The goal is to get 20 different robotic arms to maintain contact with the green spheres as long as possible. </br>
</br>
![reacher](https://github.com/p-Cyan/Udacity_DeepRL_P2_Continuous_Control/blob/main/images/reacherp_ddpg_agent_small.gif)</br>
</br>
The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.</br>

The agent is trained in the Second Version of the environment. In this version, there are 20 identical copies of the agent. For each double-jointed arm, a reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of our agent is to maintain its position at the target location for as many time steps as possible.

### Termination Condition
The environment is considered solved if a reward of +30 is obtain for 100 consecutive episodes.

## Learning Algorithm

### Deep Deterministic Policy Gradients (DDPG) algorithm.

The algorithm used here is a Deep Deterministic Policy Gradient (DDPG) [2]. A DDPG is composed of two networks : one actor and one critic. During a step, the actor is used to estimate the best action, ie argmaxaQ (s, a); the critic then use this value as in a DDQN to evaluate the optimal action value function.

Both of the actor and the critic are composed of two networks. On local network and one target network. This is for computation reason : during backpropagation if the same model was used to compute the target value and the prediction, it would lead to computational difficulty.

During the training, the actor is updated by applying the chain rule to the expected return from the start distribution. The critic is updated as in Q-learning, ie it compares the expected return of the current state to the sum of the reward of the choosen action + the expected return of the next state.

### Code implementation
The code for ddpg agent used here is derived from the ddpg-pendulum project made by Udacity. Since the model has to perform using multiple agents, it has been slightly adjusted for being used with the reacher environment. ( editted the code such that all agents simultaneously learn and update, and added noise among agents to ensure learning occurs)

The code consists of:
- model.py : This python file contains the model framework defined using pytorch.
- ddpg_agent.py : This python file contains the implementation of ddpg agent.
- Continuous_Control.ipynb : This is the jupyter implementation of the file that utilizes the ddpg agent to solve the environment.

The saved model weights are:
- checkpoint_actor.pth : Weights of the trained actor model
- checkpoint_critic.pth : Weights of the trained critic model

### Model architecture

Due to limitations in hardware and GPU hours in udacity workshop, only small networks have been trained. Luckily, these networks seemed to be sufficient to learn the tasks.

The working version of models are as follows:

```
Actor_Network(
  (fc1): Linear(in_features=33, out_features=128 )
  (fc2): Linear(in_features=128, out_features=128 )
  (out): Linear(in_features=128, out_features=4 )
)
```
```
Critic_Network(
  (fc1): Linear(in_features=33, out_features=128 )
  (fc2): Linear(in_features=128, out_features=128 )
  (out): Linear(in_features=128, out_features=1 )
)
```

### Hyper parameters

The training hyperparameters are as follow :
- Buffer size : 100,000
- Batch size : 128
- GAMMA : 0.99
- TAU : 0.001
- learning rate actor : 0.001
- learning rate critic : 0.001
- weight decay : 0

### Results

![results](https://github.com/p-Cyan/Udacity_DeepRL_P2_Continuous_Control/blob/main/images/history.JPG)

![plot](https://github.com/p-Cyan/Udacity_DeepRL_P2_Continuous_Control/blob/main/images/plot.JPG)

## Future

Other option that could be implmented are as follows:
-  [Proximal Policy Optimization (PPO)](https://arxiv.org/abs/1707.06347)
-  [Asynchronous Advantage Actor Critic (A3C)](https://arxiv.org/abs/1602.01783)
-  [Distributed Distributional Deterministic Policy Gradients (D4PG)](https://arxiv.org/abs/1804.08617)
