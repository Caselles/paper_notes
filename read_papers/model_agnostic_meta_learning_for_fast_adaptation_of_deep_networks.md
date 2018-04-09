Summary : 

Core idea -> **Our method trains the model to be easy to fine-tune.** The primary contribution of this work is a simple model-and  task-agnostic  algorithm  for  meta-learning  that  trains a model’s parameters such that a small number of gradient updates will lead to fast learning on a new task. 

How -> Sample some tasks, sample some datapoints for this task, train the networks on these points with corresponding losses. Then sample some more examples, and train the network on these examples with losses of other sampled tasks. Then, the network's parameters are "prepared", they supposedly lie in a place such that few updates on the parameters on one task and its loss provide good generalization on this task.

The method quite easily adapts to SL or RL frameworks, which is nice and different, it seems, from few-shot learning methods or most Meta-RL methods. 

The method does not add parameters to solve the Meta-Learning problem. It simply provides a clever initialization. It is nice because infinitely more simple than LSTM meta-learners that goes on top of the actual model. Clearly it makes the paper more reproducible.

Experiments : 

Experiments are done for both scenarios. 

Seems very convincing for SL, even if I'm not particulary experimented with few-shot classif and regression. First order and second order ? Does not seem clear, I will ask if I get really involved into this kind of work.

Convincing for RL too, while we may want to compare to random search algorithms to see if we really gain something.

Code is provided, thanks ! 

-----------------

Final words : 

Nice work, seems easy to implement, and seems to work well. A good step towards transfer and incremental learning that is sample efficient. Now I will read the following paper that studies the proposed method theoritically : Meta-Learning and Universality: Deep Representations and Gradient Descent can Approximate any Learning Algorithm

-----------------

Code : 

For RL : https://github.com/cbfinn/maml_rl

For other : https://github.com/cbfinn/maml

-----------------

Short Science Summary : http://www.shortscience.org/paper?bibtexKey=conf/icml/FinnAL17 

Summary Seita : https://github.com/DanielTakeshi/Paper_Notes/blob/master/reinforcement_learning/Model-Agnostic_Meta-Learning_for_Fast_Adaptation_of_Deep_Networks.md

