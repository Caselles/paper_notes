Summary: 

Setup : inputs are high-dimensional, and we want to use Stochastic Optimal Control methods (such as iLQR), which is not directly possible.

Learn an embedding of the state space, learn locally linear dynamics, and enforce the dynamics transitions with KL divergence between z_t and z_t+1.

Model : 

- VAE for x_t -> z_t : Learn mean m and variance sig of Gaussian Q(Z|X), and z_t = N(m.x_t+sig).
- Local linear model for z_t+1 : Learn mean m and variance sig of Gaussian Q(Z_t+1|Z_t,u), and z_t+1 = N(A.m+B.u+o,C).
- Generative model z_t -> x_t,x_t+1 : Learn a mean of a Bernoulli for generative model (did not understand).

You need to know the cost ............ Then you estimate the dynamics and plan. 

---------

Final thoughts: 

The proposed approach extends Stochastic Optimal Control for RGB images. Basically their approach is a way of estimating the model for a classic model-based approach in which you know R and estimate T and then plan, for a (A,S,T,R) MDP. While the approach is clever, with the locally linear dynamics, it still requires to know the cost. 

-------------

NIPS reviews : https://media.nips.cc/nipsbooks/nipspapers/paper_files/nips28/reviews/1573.html

Code : https://github.com/ericjang/e2c
