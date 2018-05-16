Summary:

Deep RL for continuous control tasks. 

They propose a methods to use Q-learning for continuous tasks, rather than policy gradient or actor-critic methods. Second contribution is the proposed use of locally linear models of the MDP dynamics to accelerate model-free methods (I'm mostly interested in that).

Problem with continuous state/action and Q-learning: greedy policy need the argmax of Q, which is intractable in the continuous case.

Solution: 

- Represent the Q-function so that the argmax is tractable. 
- Q = A(state, action) + V(state) (advantage + value). Parametrize A such that : A(state, action) = quadratic_form(feature(state)) so that Q in max w.r.t to action when action=feature(state). Nice and simple idea.


-------

Final thoughts:


--------

ICML reviews: https://icml.cc/2016/reviews/1274.txt

Code: https://github.com/carpedm20/NAF-tensorflow
