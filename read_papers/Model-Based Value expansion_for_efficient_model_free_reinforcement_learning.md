Summary:

Problem: Model-based approaches have problems, which model-free approaches does not have, and vice-versa. 

Model-based approaches suffers from prediction error, especially in long horizon. So they show a way to improve model-free Q-function estimate using H-horizon prediction using a model of the dynamics.

They define the model value expansion (MVE):

V_H(s_0) = imaginated return (model based) until horizon H + gamma_H. model-free value estimate starting from s^_H.

It is an on-policy use of the model. So they compare to DDPG.

They caracterize the value estimation error under general assumption, and such that the model errors before horizon H are small. Nice Thm giving the caracterization.

They notice a problem: the distribution of initial state mismatch. They introduce a trick in the initial distribution to solve it, and show it works with ablation study. The trick is that you should evaluate the value function estimation error under the same circumstances that you trained it with. Here we use the value function estimate starting from H-delayed states, which is not what the value function estimator was trained on. That's what they do to fix it: they set the distribution so that it's equal to the H-delayed distribution. This is done by sampling the first state as a random state between 0 and H horizon, and then using a k-step value estimate until H. The critic is trained using this sampling distribution.

Batch method, the model is not learnt incrementally.

Experiments: On MuJoCo (...)


- MVE improves Q estimates so overall performance
- The trick is necessary.

Related work:

- Dyna-like approaches: I2A, VPN
- Find a way to better the model-free learning: Gradient refinement (Stochastic value gradients), Model-ensemble TRPO


------------

Final thoughts:

This TD-k trick seems important if you have a delay in your model, have to remember it. On the paper, overall idea is not new but caracterization is nice and other evidence that this idea works is cool. Also, it is a very easy way to mix model-based and model-free, which is preferable than complicated stuff.


-------------

Under review for ICML.
