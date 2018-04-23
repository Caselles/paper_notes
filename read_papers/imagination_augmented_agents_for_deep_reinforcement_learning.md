Summary:

Tackles the problem of model imperfection in model-based RL. I see hint of the idea : using a model but not diving directly into planning in better than being pure model-free. Hence, knowing T while not necessarily knowing R helps. 

Rewards can be predicted by the I2A model.

I2A augments model-free DRL models that output value functions and policy. A imagination path is added, parralel to the classic model-free path.

How it works : Define a imagination policy for the Imagination module (here they distill the overall estimated policy into the imagination policy by adding a term in the loss function). Perform rollouts of this policy using the estimated model of the environment, which is pre-trained (you can learn jointly but they don't). Encode these rollouts using a LSTM. Concatenate these rollouts encodings and try to use them to predict the right policy and value function. 

Experiments : 
1) Sokoban. 

Why ? It seems that RGB is not useful in this case, since you can encode the maze in a vectorial form.

Every component is important, as they ablation studies prove. Reward prediction is helpful, but it still works when you remove it, at the cost of mutiplying by 3 the training time. Nice insight.

Their agent demonstrates good multi task transfer, but with no further evaluation.

2) MiniPacMan : Multi-task setting. Frames as input, defines rewards as linear combination of 5 measurements (moving, eating pill, eating ghost, ...). The models knows this. 

I2A performs better across all but one tasks. 


----------

Final thoughts:

Insight into model-based RL without reward prediction. It seems to be possible, and having a model of the environment does help. With such mechanism, lots of model-based approaches can be combined with model-free approaches.

----------

NIPS reviews: https://media.nips.cc/nipsbooks/nipspapers/paper_files/nips30/reviews/2906.html

Code: https://github.com/higgsfield/Imagination-Augmented-Agents

------

Bonus:  "Model-based RL relies on SIMULATED RETURNS." Hmmmmmmm. Give references pls.
