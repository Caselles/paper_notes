## Notes and thoughts:

I started by trying to understand current progress in disentanglement in VAEs.

There is no formal definition of disentanglement. "Towards a Definition of Disentangled Representations" propose one. Otherwise, "β-VAE: Learning Basic Visual Concepts with a Constrained Variational Framework" propose β-VAE which puts less weight on the KL term of ELBO which encourages disentanglement, and also proposes a metric. 
However in practice it does not really work as the reconstruction is often very bad. "Disentangling by Factorising" propose a better disentanglement and better metrics. But it doesn't solve the problem of reconstruction.
There are other similar approaches, such as β-TCVAE in "Isolating Sources of Disentanglement in VAEs", which suffer from the same issue but talks about disentanglement.

To fix the issue, "Understanding disentangling in β-VAE" propose CCI-VAE, where the KL term is decreased during training until good reconstruction is met. In my experience ("S-TRIGGER: Continual State Representation Learning via Self-Triggered Generative Replay"), this idea does work, although I did not try their exact method but a derivative one.

So the idea is to find balance between reconstruction and KL. It turns out that this has been thoroughly studied. "Fixing a Broken ELBO" propose a information theoretic view of the reconstruction/KL balance problem, illistrating all the issues encountered in beta-vae-like approaches. They propose a fixed-rate objective function for VAEs.
The alternative approach is given by "Taming VAEs" with the GECO algorithm, which sets a reconstruction constraint on the objective. It is theoretically better because reconstruction is interpretable and KL is not. Also "Taming VAEs" 

Remember, all this was for disentanglement. It turns out that all these approaches talking about disentanglement and that suffer from reconstruction/KL balance are not that good at what we would like disentanglement to be, as studied in "Challenging Common Assumptions in the Unsupervised Learning of Disentangled Representations".  However it is pretty disappointing not to see GECO or fixed-rate VAE in this study...

My belief is that we rather need to explore new approaches like in "Towards a Definition of Disentangled Representations", and try to study the problem theoretically first.
