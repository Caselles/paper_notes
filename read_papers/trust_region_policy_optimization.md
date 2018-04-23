Summary : 

PPO, and including TRPO tries to update the policy conservatively, without affecting its performance adversely between each policy update.

To do this, you need a way to measure how much the policy has changed after each update. This measurement is done by looking at the KL divergence between the updated policy and the old policy.

This becomes a constrained optimization problem, we want change the policy in the direction of maximum performance, following the constraints that the KL divergence between my new policy and old do not exceed some pre defined (or adaptive) threshold.

With TRPO, we compute the KL constraint during update and finds the learning rate for this problem (via Fisher Matrix and conjugate gradient). This is somewhat messy to implement.

--------------

Final thoughts : 

Messy to implement, tend to perform worse than PPO. So I guess it's kind of useless now. The idea is still used in PPO though.
