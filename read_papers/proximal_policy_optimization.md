Summary : 

PPO, and including TRPO tries to update the policy conservatively, without affecting its performance adversely between each policy update.

To do this, you need a way to measure how much the policy has changed after each update. This measurement is done by looking at the KL divergence between the updated policy and the old policy.

This becomes a constrained optimization problem, we want change the policy in the direction of maximum performance, following the constraints that the KL divergence between my new policy and old do not exceed some pre defined (or adaptive) threshold.

With TRPO, we compute the KL constraint during update and finds the learning rate for this problem (via Fisher Matrix and conjugate gradient). This is somewhat messy to implement.

With PPO, we simplify the problem by turning the KL divergence from a constraint to a penalty term, similar to for example to L1, L2 weight penalty (to prevent a weights from growing large values). PPO makes additional modifications by removing the need to compute KL divergence all together, by hard clipping the policy ratio (ratio of updated policy with old) to be within a small range around 1.0, where 1.0 means the new policy is same as old.

--------------

Final thoughts : 

Simple to use and tend to perform pretty good. The paper just describes a trick that works, which is: use TRPO loss, and clip it rather than use a hard constraint on the optimization problem.

Note: Policy gradient method, that is usually used in an Actor-Critic style. 

-------------

Code : Open AI Baselines
