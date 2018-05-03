Summary:

Problem: Model-free = inefficient but good asymptotic performance. Model-based = efficient but bad asymptotic performance because of model bias.

Link between model-based and model-free: if model-free, with value functions, can predict how easy it is to reach any state from any current state, we must have some kind of understanding of the underlying physics (dynamics T)

Method:

- They use Universal Value Functions, and define reward as the distance to goal. Then you can re-write the constrain in the model-based optimization problem (the one that says the next state should be generated according to the model) as an equation that involves the Q function. The equation is Q(s_i,a_i,s_i+1)=0. Because if the next state is the goal, then the reward is null, since the reward was defined as -D(s_i,s_g). 
- Then they proceed to extend this idea to long-horizon learning, with gamma. They do it by conditionning the Q function with the horizon, as well as the goal. In a HER fashion, every transition is usable for any horizon-goal pair (tau, s_g).
- One interesting trick they use is not learning scalar Q function but vector-valued Q function, the vector being: distance to each goal dimensions.
- Another trick is that they formulate the training so that they already have the model. Hence, they can do planning and model-free policy extraction with the same architecture, they don't have to solve the constrained MPC problem.

Experiments:
- On MuJoCo, seem to work, even if the results are not that impressive.
- On real robot, cool experiment and nice result.

-----------

Final thoughts:
Positive: Once again a paper showing that UVFs are useful. Interesting combination, even if preliminary or anecdotic, between model-based and model-free.
Negative: Seems a bit vague and not really useful.

Why not show transfer capacities between goals more clearly ? 

--------

ICLR reviews: https://openreview.net/forum?id=Skw0n-W0Z
