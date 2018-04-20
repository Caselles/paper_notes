Setup : 

Let's say you have a forward model of your environment (the dynamics are known).

i.e. f(s_t,a_t) = s_t+1 is known for a MDP.

How do you plan ?

------------------

Summary : 

Problem : Find a sequence of actions that minimizes the cumulative cost, or maximizes the return.

Deterministic case : dynamics are deterministic. Get initial state, plan, and see what you get.

Stochastic case : dynamics are stochastic. Don't commit to sequence of actions since you'd better observe how the rollout turns out.

Terminology : Closed-loop = iterative interaction between agent and env. Open-loop = commit to sequence of action.

In closed-loop, you try to find a policy that maximizes to maximize the return. The policy does not have to be a neural net ! 

[talks about model-free methods... Why ?]

Can we use derivatives, since we know f ? 

Problem : min_{u1,..,uT} c(x1,u1) + c(f(x1,u1),u2) + .. + c(f(f(..)),..),u) > can back-prop ! 

But very sensible to initial state (exploding gradients).

Instead, use 2nd order methods.

Shooting versus collocation methods : 

- shooting optimize over actions, so launches trajectories.
- collocation optimizes over states and actions, so pins states in the trajectory.

Linear case : LQR. Dynamics are linear, cost is quadratic. How to solve the shooting problem ? 

Find the optimal last action as a function of the last state. The best last action is fully determined by the last state.
Maths : write the Q function Q(x_t, u_t), it happens that the best action can be written only in terms of x_t because of the LQR. So we get the value function on x_t.

Then solve the u_t-1 action in terms of x_t-1. u_t-1 affects x_t ! But we known how because we have f. 
Maths : Write the Q function Q(x_t-1, u_t-1) = V(f(x_t-1, u_t-1)) + cost. We know everything, so problem solved, we find the best second to last action and do recursion (we have the first state to initialize :) ).

Works also with stochastic dynamics (p(x_t+1|x_t,u_t)=N(A.x_t+B.u_t))

What if we don't have linear dynamics nor quadratic cost ? (Finally)

DDP and iterative LQR algorithms.

Idea of iterative LQR : locally approximate f and c as linear and quadratic, with taylor expansions around some trajectories. Update trajectory each time you get new state.

Related to Newton's methods, but does need Hessian. Hessian is a big tensor so it's a pain, and in practice the first order derative is enough. 

DDP is iLQR with Hessian.

DO YOU NEED C OR NOT ??? It seems that you need it. Alright I am very dissapointed.


