Summary:

They compare different type of models for, ultimately, model-based RL. They compare deterministic, stochastic, pixel-space or state-space models.

They compare:

- Auto-regressive (AR) models: p(o_t+1:t+tau | o_<t, a_<t+tau) = PI_r(p(o_r | f(o_<r, a<r)) > pixel-space so slow rollout.
- Recurrent AR: p(o_t+1:t+tau | o_<t, a_<t+tau) = PI_r(p(o_r | f(o_<r, a_<r, h_<r)) > RNN on pixel-space.
- Deterministic/stochastic state-space models: p(o_t+1:t+tau | o_<t, a_<t+tau) = Int(PI_r((p(s_r | s_r-1, a_r-1).p(o_r | s_r)).p_init(s_t | o_<t, a_<t))). They are composed of the transition model: s_t+1=g(s_t,a_t,z_t+1) in the case of stochastic, and without the z_t+1 in the case of deterministic, and an observation model (decoder) that maps s_t to o_t.
- They use jumpy training which means they chunk sequences of length c. This reduces the computational cost of rollouts by a factor of c.
- Architecture is all convolutional. They use pool-and-inject layers to overcome the limitation of small receptive fields associated with the convolutions.

They use I2A as a RL agent. They show that comparing to a baseline they have better performance on MS Pacman.

--------

Final thoughts:

They show that among all possibilities, stochastic SSM seems better suited to model-based RL for Atari. 

-------

Review (ICLR 2018, reject): https://openreview.net/forum?id=HJw8fAgA-
