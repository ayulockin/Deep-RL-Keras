# Advanced Deep RL in Keras

Implementation of various Deep Reinforcement Learning algorithms:

- [x] N-step Advantage Actor Critic ([A2C](https://github.com/germain-hug/Advanced-Deep-RL-Keras#n-step-advantage-actor-critic-a2c))
- [x] N-step Asynchronous Advantage Actor-Critic ([A3C](https://github.com/germain-hug/Advanced-Deep-RL-Keras#n-step-asynchronous-advantage-actor-critic-a3c))
- [ ] Deep Deterministic Policy Gradient with Parameter Noise ([DDPG](https://github.com/germain-hug/Advanced-Deep-RL-Keras#deep-deterministic-policy-gradient-ddpg))
- [ ] REINFORCE
- [ ] Deep Q-Learning (DQN)
- [ ] Dueling DQN (DDQN)
- [ ] Rainbow
- [ ] Proximal Policy Optimization (PPO)
- [ ] Impala
- [ ] Spiral

### Prerequisites

This implementation requires keras 2.1.6, as well as OpenAI gym.
```
pip install gym keras==2.1.6
```

## N-step Advantage Actor Critic (A2C)
The Actor-Critic algorithm is a model-free, off-policy method where the critic acts as a value-function approximator, and the actor as a policy-function approximator. When training, the critic predicts the TD-Error and guides the learning of both itself and the actor. In practice, we approximate the TD-Error using the Advantage function. For more stability, we use a shared computational backbone across both networks, as well as an N-step formulation of the discounted rewards. We also incorporate an entropy regularization term ("soft" learning) to encourage exploration.  

```bash
python3 A2C/main.py --env CartPole-v1 --nb_episodes 10000 --render
```

<br />
<div align="center">
<img width="30%" src ="https://github.com/germain-hug/Advanced-Deep-RL-Keras/blob/master/A2C/results/a2c.jpg?raw=true" />
<img width="30%" src ="https://github.com/germain-hug/Advanced-Deep-RL-Keras/blob/master/A2C/results/a2c.gif?raw=true" />
<p style="text-align=center";> Average Score per Episode (Cartpole-V1) and Results </p></div>  
<br />

Link to [[paper]](https://papers.nips.cc/paper/1786-actor-critic-algorithms.pdf)

## N-step Asynchronous Advantage Actor Critic (A3C)
In a similar fashion as the A2C algorithm, implementation of A3C, incorporating asynchronous weight updates. We use multiple agents to perform gradient ascent asynchronously, over multiple threads.

```bash
python3 A3C/main.py --env CartPole-v1 --nb_episodes 10000 --n_threads 16
```

Link to [[paper]](https://arxiv.org/pdf/1602.01783.pdf)

## Deep Deterministic Policy Gradient (DDPG)
The DDPG algorithm is a model-free, off-policy algorithm for continuous control. Similarly to A2C, it is an actor-critic algorithm in which the actor is trained on a deterministic target policy, and the critic predicts Q-Values (using TD errors). In order to reduce variance and increase stability, we use experience replay and separate target networks. Moreover, as hinted by [OpenAI](https://blog.openai.com/better-exploration-with-parameter-noise/), we encourage exploration through parameter space noise (as opposed to action space noise).


# Acknowledgments

# References

- _Advantage Actor Critic (A2C)_ : [[paper]](https://papers.nips.cc/paper/1786-actor-critic-algorithms.pdf)
- _Asynchronous Advantage Actor Critic (A3C)_ : [[paper]](https://arxiv.org/pdf/1602.01783.pdf)
- _Deep Deterministic Policy Gradient (DDPG)_ : [[paper]](http://proceedings.mlr.press/v32/silver14.pdf)
