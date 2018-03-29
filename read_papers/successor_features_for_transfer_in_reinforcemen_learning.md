# Summary : 

## 1) Intro : 

What is transfer learning and why it is important : good description. 

## 2) Background and problem formulation :

Definition of MDP and transfer learning in the scope of this article. 

 Let T,T' be two sets of tasks such that T' included in T, and let t be any task. Then there is transfer if, after training on T, the agent always performs as well or better on task t than if only trained on T'.

## 3) Successor features : 

Decoupled (environnement, reward) parametrization of the reward function : r = phi . w

Hence, we can also have a decoupled parametrization of the Q function, that relies on phi : Q = psi . w

Note that w encodes everything about the reward and phi (or psi) encodes everything about the environnement. It allows for a simple formalization of MDP where you learn phi or psi for some reward w_i, and then you can use phi or psi on another task w_j, and hopefully you perform better than if you would have not seen w_i. This is why this formulation is useful for transfer in RL.

## 4) Transfer via successor features

The proposed method for transfer learning, and theoretical guarantees that come with it.

Suppose that we have learned the functions Q_i^Pi_i using the representation scheme shown in (3) (which is Q = psi . w_i). Now, if the reward changes to r = phi . w_n+1, as long as we have w_n+1, we can compute the new value function of Pi_i by simply making Q_n+1^Pi_i  = psi . w_n+1. This reduces the computation of all Q_n+1^Pi_i to the much simpler supervised problem of approximating w_n+1. Once we have all Q_n+1^Pi_i, we compute the new better transferred policy using Theorem 1 (acting greedily according to all Q functions yields a better policy than all the rest).

This strategy comes with guarantees : the learnt policy's Q function is good relatively to the optimal policy's Q function, and the error bound is a multiple of the minimum distance between the new task and other tasks that are used for transfer. It means that in the policies that we learn from, if one is for a task that is close to the task we want to transfer to, then this strategy will perform well. It is quite a neat result because it relates a distance in R^d to a difference of performance in the environnement. So it allows for algorithm design. I will have to look on that.

## 5) Experiments

1 simple experiment : lots of details in Appendix B. Think it can be reproduces. They use simple algorithms (Q-Learning) and no neural networks, cool to see such simple interpretable experiments. 

1 "hard" experiment : get a robotic arm to reach a position in MuJoCo. See appendix B. They compare to DQN, and fit DQN with the SF paradigm.

In both experiments they show that SF outperforms the rest.

## 6) Related work :

Have to go back on that later. Relation to GVF and UVFA, and transfer learning methods.

## Final words :

Interesting, not impossible to implement, theoretically sound. I like this work and it would be interesting to incorporate new elements in it. It indeed seems like a good framework for transfer in RL, since it incorporates to RL easily both practically and theoretically. 

----------------------------

NIPS reviews : https://media.nips.cc/nipsbooks/nipspapers/paper_files/nips30/reviews/2151.html

----------------------------

No implementations found.

