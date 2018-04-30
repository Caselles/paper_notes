# Summary : 

## Overview on options: 

Options is a temporally abstracted reinforcement learning framework. 

Definition of option: initation set I, policy pi, termination condition beta. Starting from a state in I, you follow pi until beta triggers.

Definition of option model : (A,S,P_o, R_o). P_o(s) is the transition model, aka a sub-proba distribution over next states given that o executes from s. It specifies when and where the agent will end up after the option is executed. R_o(s) is the expected return of o starting from s.

Options provide semantics : You can sequence two options, it results in one option with r = r_o1 + P_o1.r_o2 and P = P_o1.P_o2.

MDP + options = SMDP. Hence ALL PLANNING AND LEARNING ALGORITHMS FROM CLASSICAL MDP APPLY TO OPTIONS. But they can be faster if you find the right options, which is the whole point.

Reward option model: Expected return of following o: r_o(s) = E[r_t + ... + ... | s_t=s, o_t=o]. You can write a Bellman equation for the return, because it is basically a value function. So you can use RL methods to learn models of options.

Intra options algorithms: Given a set of options, can we learn about all options consistent with the current behaviour ? In tabular case, you can write the ~~action-value~~ option-value function Q. In general function approximation, you need to use importance sampling, but possible. 

## Frontier: Option discovery

What is a good set of subgoals ? Representation discovery problem. How to break up problems into sub-problems so that we facilitate learning ? Most successful methods use bottleneck states and change point detection.

## Current work:

Goals: Optimization objective, then solve it to find a set of options. Handle both continous and discrete set of states and actions. Learning options in a continual way, not combinatorial. Should improve also in one task.

Inspired by actor-critic algorithms that complete each goals.

They propose Option-Critic : 

- learn option-value function Q, gradients to optimize options policies and termination conditions, then select the behaviour policy.
- the gradients can be computed : w.r.t policy you do more of the action that give a lot of value, w.r.t to termination condition you finish less of the options that give a lot of advantage (lengthen options that have large advantages).

Results: 

- Option transfer in grid-world maze: after goal gets moved, options find new goal faster.
- Atari: Same or better than DQN (meh). Options for are intuitive.

Problem:

- Option shrink over time and dissolve into primitive actions because primitive actions allow for optimal return. 
- How to encourage longer options ?
- You can flatten policies, and show that the Bellman equation is equivalent to a matrix splitting. Then choosing a particular set of options is equivalent to choosing a particular splitting of matrices. It leads to longer options = fewer iterations.
- Deliberation cost: executing a policy is cheap, deciding what to do is expensive. Define c(s,w) the cost of deliberating to choose o in s. Then this cost has a value function associated to it, with a Bellman equation. So new ojective: maximize reward with reasonable effort (regularization with a parameter).
- Experiments: using deliberation cost shifts policy towards using options, and number of iteration is smaller. Also better transfer properties.

Future work:

- Matrix splitting seems like a great mathematical framework for options.


-----------

Final thoughts : 


Options seem interesting even though option discovery is the main issue. It seems like the way to go to create really interesting behaviour. Options does not seem to be popular in the RL community, so there might be a lot a possible ideas to use them in combination with other ideas.
