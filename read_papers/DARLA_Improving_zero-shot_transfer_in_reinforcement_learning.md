Summary : 

Problem: Domain Adaptation. Changes in high level parameters of the environment, colors, shapes for instance.

How to learn general representations suitable for describing all domains ? Disentanglement is their solution. (They are authors of Beta-VAE).

Method: 

- Learn to see: train a Beta-VAE-DAE, i.e. a Beta-VAE that tries to match the latent space of a pretrained Denoising AutoEncoder. See Figure: 

![](https://github.com/Caselles/paper_notes/blob/master/images/4.png)

- Learning to act: use RL to train a policy Pi with learnt latent space as input.
- Transfer: Try Pi on a different domain and see results. 

Experiments: 

- DeepmindLab: Seek-avoid navigation task. Shows transfer, but the source domain seems really close to the target domain. 
- Sim2Sim MuJoCo Jaco arm: Object reaching. Transfer is different viewpoints. 
- Sim2Real: same, but more interesting. Not that much gain with their method, but still I don't think it is the most interesting way to evaluate this.

--------

Final thoughts : This is easy to understand and gives good insights. 

I understand that beta-VAE does not work without the DAE trick. I should try this. 

My main comment is why do they try to transfer policies ? IMO we don't want policies to be general (as in able to be transfered from one domain to another), but rather the learnt latent space, which seems to be the case here. I would have tried experiments where I compare a RL (on domain Target) with entangled latent space (learnt in domain Source) as input to RL (on domain Target) with a disentangled latent space (learnt in domain Source) as input.

The notation are interesting for Domain Adaption.

------

Conference: ICML 2017.

Code: I have code from my lab for this. Contact me if interested.
