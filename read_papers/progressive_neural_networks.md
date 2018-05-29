Summary:

In order to solve catastrophic forgetting in neural nets, they propose an architecture for continual learning. 

What's interesting is that they evaluate on RL tasks (Atari (across tasks and within a task with mutiple texture etc) and Mazes).

The architecture uses a brute force approach:

- Whenever we add a task, we add a whole new model and connect all the previous outputs to the new next layer.

![](https://github.com/Caselles/paper_notes/blob/master/images/1.png)

- The transitions between activations of side layers and the new model are smoothed by adding parameters used for scaling the inputs ("a" boxes).

Experiments: 

- Setup: to assess the contribution of previous layers they use two metrics, one base on perturbation of the weights (slow) and one based on the Fisher information to approximate rapidly the former. Their performance metric is AUC of training curve, not final performance (not standard). Their transfer learning metric is the relative performance to a single-column model.

- Experiments: Main result is that PNN transfer as well as fine-tuning while retaining previous knowledge (by design). Expected result is met.

-------

Final thoughts:

Brute force approach to continual learning, which works. Experiments are very thorough so it's nice to have the method showcased in many scenarios. Thus, it's viable way to incorporate continual learning in a NN.

Q: Works with CNNs and MLPs. LSTM are okay too ? 

-----------

Morning paper article: https://blog.acolyer.org/2016/10/11/progressive-neural-networks/

Code (toy): https://github.com/howland/DQN_PNN
