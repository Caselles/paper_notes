Summary:

Goal: A forward model with long-term memory (no LSTM) for a complex environment (ex: predict 100 timesteps into the future in a 3D maze).

Gemici et al. confirm that using external memory fails for complex environments.

They use: a VAE, a state-space model (i.e a forward model in the latent space that models p(o_t+1:t+tau | o_<t, a_<t+tau), see "Learning and Querying Generative Models for RL"), and the DND (see Neural Episodic Control).



--------

Final thoughts:



---------

Nothing found online on this work but tweets.
