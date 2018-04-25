Summary : 

DSR : Hybrid model-free / model-based system. They use Successor Representations, which decouples the value function into two components: a reward predictor and a successor map.

Model-based : estimate T and R and plan. Model-free : estimate nothing and find out policy. The system is "goal-agnostic", which means it can rapidly adapt to new reward functions and estimates T.

Q(s,a) = sum_s' (M(s,s',a)R(s') >> M is the future state visitation count, and R the immediate reward at s. Logic. 

Proposed architecture: 

- State Representation Learning into the model, like a VAE, yields phi
- Learn an approximation m of M as a function of phi (NN) 
- Learn R as phi.w

Then performed Q-learning à la DQN., with the loss for R, for VAE and Q-learning.

One thing DSR can do is to extract subgoals automatically. Given a random policy ran in the env, generate an affinity matrix with the m collected. Get an approximation of the minimum normalized cut value of the partition T (collected m). States that often lie along the cut can be sub-goals.

Experiments: nothing ultra impressive but,
- Show on-par performance with DQN on grid-world maze and vizDoom maze.
- Show robustness to reward scale changes.
- Show automatic sub-goal detection on grid-world maze.

Conclusion: you should use this for hierarchical RL. (would have been nice to show it in experiments)

------------

Final thoughts : 

May be useful for Hierarchical RL framework. What is interesting for me is that the system is goal-agnostic. It could be better shown I think. But still using Q-learning seems like a wrong approach to solving a lot of sparse RL tasks sampled from the same task distribution (multi-task learning), because it seems slow and non-robust. It if struggles on one taks then how could it transfer well to changes of tasks ?

-------------

Code : https://github.com/Ardavans/DSR
