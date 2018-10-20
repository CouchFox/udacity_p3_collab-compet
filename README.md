[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/42135623-e770e354-7d12-11e8-998d-29fc74429ca2.gif "Trained Agent"


# Deep Reinforcement Learning Nanodegree
## Project 3 Readme

![Trained Agents][image1]

This repository contains material related to Udacity's [Deep Reinforcement Learning Nanodegree] (https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893) program Project 3 .  


### Project Details

The goal of this project was to train a DRL-Networt for an environment with two agent to play tennis.

In this environment, two agents control rackets to bounce a ball over a net. If an agent hits the ball over the net, it receives a reward of +0.1. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play.

The observation space consists of 8 variables corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation. Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping.

The task is episodic, and in order to solve the environment, the agents must get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents). Specifically,

- After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent. This yields 2 (potentially different) scores. We then take the maximum of these 2 scores.
- This yields a single score for each episode.

The environment is considered solved, when the average (over 100 episodes) of those scores is at least +0.5.




### Getting Started
To install the code for Project 2 of the Udacity Deep Reinforcement Learning Nanodegree, follow the instructions here: https://github.com/udacity/deep-reinforcement-learning

I chose to install the code locally on an Ubuntu 16.04 with an NVidia 1080 Ti graphics card. To setup tensorflow with gpu, cuda and cuDNN I followed this instructions:
https://medium.com/@zhanwenchen/install-cuda-and-cudnn-for-tensorflow-gpu-on-ubuntu-79306e4ac04e

To install this repo just git clone it and copy the content (incl. the two folders) to the deep-reinforcement-learning folder from above.

then use conda with the provided environment.yml to install the dependencies:
```
conda env create -f environment.yml
```



### Instructions

**To run the code:** start the jupyter notebook called Tennis.ipynb and run the cells. Skip step 3 if you're not interested in random actions (or can't display them).


### Resources
- Unity's ML-Agents: https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Installation.md
- Unity's PuppoDemo: https://blogs.unity3d.com/2018/10/02/puppo-the-corgi-cuteness-overload-with-the-unity-ml-agents-toolkit/.
