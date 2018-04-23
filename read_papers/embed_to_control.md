Summary: 

Setup : inputs are high-dimensional, and we want to use Stochastic Optimal Control methods (such as iLQR), which is not directly possible.

Learn an embedding of the state space, learn locally linear dynamics, and enforce the dynamics transitions with KL divergence between z_t and z_t+1.

---------

Final thoughts: 

-------------

NIPS reviews : https://media.nips.cc/nipsbooks/nipspapers/paper_files/nips28/reviews/1573.html

Code : https://github.com/ericjang/e2c
