[//]: # (Image References)

[image1]: result.png "Result"
[image2]: plot.png "Plot of Rewards"

# Deep Reinforcement Learning Nanodegree - Project 3 Report
The goal of this project was to train a DRL-Networt for an environment with two agent to play tennis.

In this environment, two agents control rackets to bounce a ball over a net. If an agent hits the ball over the net, it receives a reward of +0.1. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play.

The observation space consists of 8 variables corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation. Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping.

The task is episodic, and in order to solve the environment, the agents must get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents). Specifically,

- After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent. This yields 2 (potentially different) scores. We then take the maximum of these 2 scores.
- This yields a single score for each episode.

The environment is considered solved, when the average (over 100 episodes) of those scores is at least +0.5.

## Learning Algorithm
For this Project the DDPG (Deep Deterministic Policy Gradient) is used to solve the environment.
An advantage of DDPG over say DQN is that it doesn't rely on discretisation. Instead it can directly deal with continuous inputs. DDPG is an actor-critic architecture with the actor to be used to learn the parameter theta for the policy function. The critic is then used to evaluate the policy function of the actor.

The code is based on the agent and model from the ddpg-bipedal source for the ai gym. Both network models for the actor and the critic consist of simple fully connected layers with 2 hidden units each.
The modifications consisted of the following changes:
- instead of a gym environment, the unity environment had to be used. (see comment in notebook for alterations)
- the model for the critic and actor were chosen smaller for this environment:
 - actor: 256 x 128
 - critic: 128 x 64
- I added a batchnorm layer to the actor and critic network to make it more stable
- the hyperparameters were chosen as follows (they could be reused from project 2):
```
BUFFER_SIZE = int(1e6)  # replay buffer size - didn't need change
BATCH_SIZE = 1024       # minibatch size before 128 - seems to run more stable when higher
GAMMA = 0.99            # discount factor - no change
TAU = 1e-3              # for soft update of target parameters - no change
LR_ACTOR = 1e-3         # learning rate of the actor - worked better with 1e-3 than 1e-4 in ddpg-bipedal
LR_CRITIC = 1e-3        # learning rate of the critic - no change
WEIGHT_DECAY = 0.000    # L2 weight decay - set to zero as in ddpg-pendulum
```


## Plot of Rewards
Before adding batchnorm to both actor and critic, the model seemed highly unstable.

Here you can see the last training episodes:
![Results][image1]


And here is the plot of rewards while training:
![Plot of Rewards][image2]


## Ideas for Future Work
- solve the project with alphazero instead of ddpg
- modularize other algorithms into agent and model classes for easy replacement in code
- adapt the code learnt in the udacity lessons to tensorflow
- train with other games e.g. nine men's morris
