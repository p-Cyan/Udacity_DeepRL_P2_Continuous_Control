## Udacity Deep Reinforcement Nanodegree
</hr>
This repository contains my project submission for project 1 of Udacity's [Deep RL Nanodegree program](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893)

## Project 2: Navigation

</hr>

### Environment Details
This is a [Unity ML Agent](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#reacher) Reacher environment provided by Udacity. The goal is to get 20 different robotic arms to maintain contact with the green spheres as long as possible. </br>
</br>
![reacher](https://github.com/p-Cyan/Udacity_DeepRL_P2_Continuous_Control/blob/main/images/reacherp_ddpg_agent_small.gif)</br>
</br>
The agent is trained in the Second Version of the environment. In this version, there are 20 identical copies of the agent. For each double-jointed arm, a reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of our agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.</br>

The environment is considered solved if a reward of +100 is obtain for 30 consecutive episodes.

The method to use is an actor-critic algorithm, the Deep Deterministic Policy Gradients (DDPG) algorithm.

## Getting Started

</hr>

### Installation requirements
- You first need to configure a Python 3.6 / PyTorch 0.4.0 environment with the needed requirements as described in the [Udacity repository](https://github.com/udacity/deep-reinforcement-learning#dependencies).</br>
- You then have to clone this project and have it accessible in your Python environment</br>
 -Download the environment from one of the links below. You need only select the environment that matches your operating system:
  - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
  - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
  - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
  - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)
- Then, Follow the instructions in Continuous_Control.ipynb to get started with training your own agent!

### Misc : Configuration used
This agent has been trained on the Udacity provided online workspace. This environment allows to use a Nvidia K80 GPU that is used for the training. (The headless / no visualization version of the Unity environment was thus used)

My setup is a "Deep Learning Dev Box", and is basically a Linux GPU Server, running Docker containers (using Nvidia Docker 2), serving Jupyter Lab notebooks which are accessed remotely via a web interface (or a ssh connection) : unfortunately this setup does not seem suitable to run Unity ML agent, with the GPU and providing a display for for the agent (See [Unity documentation](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Using-Docker.md) for more details)


