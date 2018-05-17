Summary:

Deep RL for continuous control tasks. 

They propose a methods to use Q-learning for continuous tasks, rather than policy gradient or actor-critic methods. Second contribution is the proposed use of locally linear models of the MDP dynamics to accelerate model-free methods (I'm mostly interested in that).

Problem with continuous state/action and Q-learning: greedy policy need the argmax of Q, which is intractable in the continuous case.

Solution: 

- Represent the Q-function so that the argmax is tractable. 
- Q = A(state, action) + V(state) (advantage + value). Parametrize A such that : A(state, action) = quadratic_form(feature(state)) so that Q in max w.r.t to action when action=feature(state). Nice and simple idea.

Another thing they propose to use to mitigate the sample-efficiency problem:

- Adding on-policy rollouts of a locally learned model to the experience replay
- They stop doing this at some point (a fixed number of epochs)
- They fit a time-varying locally linear model: a Gaussian N(F_t(x_t,u_t)+f_t, N_t)

Experiments:

- NAF has same performance compared to DDPG on MuJoCo. Some minor differences but the main point is you can successfully learn Q-function in continuous state/action scenarios with NAF, which is enough to be impressive on its own.
- They show that using off-policy rollouts of a perfect model and adding them to the experience replay does not work, which is very interesting. The reason might be that you need errors and bad actions in the experience replay for Q-learning to successfully learn.
- Then they show that their proposed method of mixing model-based imaginated on-policy rollouts make training more sample efficient, by a small margin IMO. Nevertheless it is promising and that's why we see mutiple papers (2018) on mixing model-based and model-free.


-------

Final thoughts:

Ideas are very interesting, and the experiements are a good proof of concept. 

Main novel thing is Q-learning for continuous state/action. It does not seem that NAF is very used as of right now (2018).


--------

ICML reviews: https://icml.cc/2016/reviews/1274.txt

Code: https://github.com/carpedm20/NAF-tensorflow
