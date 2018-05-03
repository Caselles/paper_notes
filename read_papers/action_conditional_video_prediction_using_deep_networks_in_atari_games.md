Summary:

Idea: two spatio-temporal prediction architectures based on deep networks that incorporate action variables.

Goal: approximately capture natural similarity among actions, and discover which objects are directly controlled by the agent’s actions and which are only indirectly influenced or not controlled

Model:
- Learn a function f(x_1,..,x_t,a_t)=x_t+1
- CNN encoder, then LSTM, then multiplicative action-conditional transformation, then CNN decoder. Logic.
- Curriculum learning: first learn how to predict in near future and after convergence learn how to predict in the long-horizon future.

Experiments:

- Atari: hyper realistic. Compare to baselines, nothing really interesting.
- Replacing real frames by predicted frames for DQN: score below, unsurprisingly, but close to the results obtained with real frames.
- Intrinsic motivation: go to frame that have not been visited a lot in the last d steps. Helps DQN.

----------

Final thoughts:

High-dimensional sensorimotor prediction model. Seem to work well. But it has not been used successfully later... So it might not be very useful ? 

At least for me it seems useful. If you define goals in terms of future states for example you could use this model to navigate in the env, i.e solve a bunch of sparse reward RL tasks. 

-----------

Code: https://github.com/junhyukoh/nips2015-action-conditional-video-prediction

NIPS review: ??? Can't find it.
