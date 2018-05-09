Summary:

Nice and thorough related work on learning skills. 

Key idea: maximize distinguishability, and diversity.

Formulation of the objective, use of variational lower bound to be able to compute the objective.

Once the skills are learned, you can use them for different tasks specified by reward functions. Method: evaluate all skills on specific a reward function and choose the best performing skill (this step is cheap compared to training a RL agent), and initialize the weights of a RL agent with this skill. Then, compared to a random initialization, learning happens faster (I would have expected it to be even faster, but it's faster anyway).

You can learn to imitate skills easily too, by using the most resembling skill to the expert policy.

--------

Final thoughts:

Learn skills in an unsupervised manner, with a simple information theoretic objective. Trick: use this objective has reward for a RL algo. Neat.

Transfer learning is done by pretraining the model to learn skills, and then select the most suited skill as initalization. It's still pretty reward specific since you need to train the model on the reward function, not like DFP where it performs well directly.

---------

Summary and author note: https://github.com/flrngel/understanding-ai/issues/7

Author code, and comments on future work: https://github.com/ben-eysenbach/sac/blob/master/DIAYN.md
