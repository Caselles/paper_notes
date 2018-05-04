Summary:

Idea: 

- Dynamics module: Learn off-policy a forward model: s_t > CNN > z_t > LSTM > z^_t+1 > CNN > s^_t+1 + inverse model (z_t, z_t+1 > MLP > a^_t)
- Reward module: Learn on-policy a reward module: actor-critic over z_t, with a LSTM (for some reason).

Experiments:

- MuJoCo, show that it's better than A3C.
- Transfer: show that if you change reward it works better than fine-tuning A3C (quite unfair).
- Show that inverse model is important, performance drops if not in the dynamics module.

--------

Final thoughts:

The idea that the inverse model helps a lot is very interesting. It's an auxiliary task for the forward model that improves the feature space. 

Basically what they do is SRL with a sensorimotor prediction module. So it is highly related to want I want to do. The work can be extended in many many ways.

--------

ICLR review: https://openreview.net/forum?id=H1aoddyvM
