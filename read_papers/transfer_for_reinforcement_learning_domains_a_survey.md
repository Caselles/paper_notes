Summary : 

# 1/ Intro

Overview on RL and TL.
Approaches to solve problems of the PhD. 
Why is TL important ? 
How TL tasks are different ? 

# 2/ Evaluation

Full autonomous agent : 3 sub-problems. In reality people try to solve one of the 3, because it is hard.

1: Given a target task, select appropriate source task(s) from which to transfer
2: Learn how the source task(s) and target task are related
3: Effectively transfer knowledge from the source to the target

Total time vs target time ? Source task learning time should not be a sunk cost.

## 2.1/ Empirical transfer evaluation

Possible benefits of TL : Jump start, Asymptotic performance, Total reward, Transfer ratio, Time to threshold. Why not performance profile ? No unique metric, each is important.

Learning time = Sample complexity

Insights on problem with each metric.

Proposed metric : Ratio = (AUC with TL - AUC without TL)/(AUC without TL) >> Better, but still not scale invariant.

No comparison of TL algorithms between them in the literature.

## 2.2/ Dimensions of comparison

5 dimensions : Task difference assumption, Source task selection, Task mappings, Transferred knowledge, Allowed learners.

# 3/ Transfer for RL

## 3.1/ RL Background

RL framework definition.

Algorithms for MDPs: Temporal difference, Policy search, Dynamic Programming, Model-based, Relational RL, Batch learning methods.

In 2009 DQN things were already done. Just not with CNNs.

## 3.2/ Transfer approaches

What can change and be considered as transfer ? Basically everything. Infinite number of scenarios.

Can a TL guarantee that a source task is useful ? Open question. Some neat results in Successor features for TL.

Type of transferred knowledge ? Low (transitions) vs high (options) level knowledge.

## 3.3/ Multi-task learning

Multi-task learning is included in TL ! Tasks are sampled from the same distribution. 

Often considered sequentially. Some bonus with this restriction is that it can be be used in a more rigourous theoretical framework, such that, in the end, SF for TL. In fact, according to this survey SF for TL should be called SF for MTL.

## 3.4/ Inter-task mappings

If source and target tasks do not have same state space and action space, we need inter-task mappings. 

Either told how the tasks are related, or learns it. Have to define what "similar" actions or states are. For that, Q value, transition, or reward can be used. 

## 3.5/ Related paradigms

Life-long learning (I'm interested in that): TL included in LLL. TL is single pair of tasks, and TL is told when the new task has begun. In LLL you can have lots of tasks and agents may have to automatically identify new sub-tasks in the global MDP (i.e. the real world).

Imitation learning: agents learn by watching another agent abilities. Related to TL but different: TL wants to re-use past learned knowledge.

Human advice: Humans in the loop, that can help give feedback to the agent. Not automous but can achieve complex learned behaviours.

Reward shaping: Humans modify task to allow better learning.

Representation transfer: Transferring knowledge between agents with different internal representation (ie algos) of the same task.

# 4/ Transfer methods for fixed state variables and actions (survey begins)

Selfridge (85): Changing the task transition function T over time, from easy to hard. Lead to quicker training.

Asada (94): Learning from easy missions, humans constructing a set of tasks for the learner. Move the initial state further away each time to the goal. It incrementally learns how to navigate faster than when he has a lot of exploration to do. Relies on human but have this incremental flavor.

Singh (92): Breaking a task into smaller sub-tasks. Detecting sub-tasks can be done automaticaaly if there are patterns in any signal that can identifiy sub-tasks. For instance, in a 2D navigation task each room may be a sub-task and the steep value function gradient between impassable walls is easily identifiable.

Atkeson and Santamaria (97): Transfers a locally weighted regression model of T, learned in the source task, by directly applying it to the target task. Allows for planning, and show improvement in terms of jump start, total reward and asympotitic performance.

Asadi and Huber (07): Transfers partial policies or options. Hierarchical Bounded Parameter SMDP. Automatically identifies sub-goals in the source task and then learn options to reach these sub-goals. 

Andre and Russell (02): Transfers options between tasks. This work highlights the connection between state abstraction and transfer, if similarities exists between parts of the state space in the two tasks, good local controllers ore local policies or options can be directly transferred. 

Ravindran and Barto (03): Learn relativized options in a small source task. When learning in the target task, the agent is provided these options and a set of possible trasnformation of the options that can be relevant in the target task. If source is a small maze, then target can be a similar looking bigger maze, and transformations can be rotation, reflection, etc.

Mahedevan and Maggioni (07): Proto-value functions. specify a set of basis functions, without regard to R, which can be used to learn an action-value function. Then PVF can be used in other tasks. Seems like SRL or SF for TL. 

Sherstov and Stone (05): Rather than reasoning over the proba of reaching a given state after an action, the learner reasons over the actions' effect, or outcome. States are grouped together in classes such that the proba of a given outcome from a given action will be the same for any state in a class. It allows to reduce the action space, and they have theoritical results. See paper ! Follow-up paper by Leffler (07) where they apply the framework to learn a single task faster, both on simulation and real world. An interesting idea here is to attempt to automatically generate the source tasks (with DFP maybe?). How to best generate the source task is an open problem.

Madden and Howley (04): Progressive RL is a method for transferring between a progression of tasks of increasing difficulty, but is limited to discrete MDPs. Allows for Incremental Learning in discrete MDPs, if a new state in encountered it initialize the Q-value of that state so that the action suggested by the learned rule is preferred.

Lazaric (08): Instances (<s,a,s',r>) from the source tasks that are the most similar to target task, judged by their distance and alignment with target task data, are transferred. Thus, similar regions in the source task are transferred. It might be different regions from different tasks, thus the relevance of the method. It uses batch learning. 

Idea they provide: combine everything together ? meh. Give exact ideas though. See that if no inspiration.

# 5/ Multi-task Learning methods

Mehta (08): Variable-reward hierarchical reinforcement learning assumes the learner will train on a sequence of tasks which are identical except for different reward weights. Reward weights encode for the task via a linear combination of reward features, similarly to SF for TL. When a novel task is presented, the agent sets the initial policy to that of the most similar source task, as determined by the dot product with previously observed reward weight vectors. 

Perkins and Precup (99): T might change after reaching the goal. The agent is provided with a set of hand-coded options which assist in learning on this set of task created by modifications of T. Over time, the agent learns an action-value function over these options. 

Foster and Dayan (04): aim to identify sub-tasks in the source task and use this information in the target task, similarly to Singh (92). Tasks are allowed to differ in the placement of goal states. Learns sub-tasks with EM algo. 

Fernandez and Veloso (06): Probabilistic policy reuse. Consider a distribution of tasks where only the goal state differs, if a new policy is significantly different from existing policies, it is added to the policy library. When the agent is placed in a novel task, on every timestep, it can choose to: exploit a learned source task policy, exploit the current best policy for the target task or randomly explore. It probabilistically selects between policies so that over time more useful policies will be selected more often. The idea of having a sorted by quality and usefulness policy library is indeed interesting. You could learn the optimal library to perform well across a set of tasks.

Tanaka and Yamamura (03): Gather statistics about all previous tasks and use it to learn novel tasks faster. Set action-value function to average value in every task. In a new task, initalize Q-function to this average value. Then prioritize TD udpates to state-action pairs that are far away to the average, because they are likely to be incorrect (if the target task is related to the source tasks, I guess).  Also use the variance of the Q-values, if they are big it's likely that you need to update this particular state-action because it is likely not estimated correctly.

Sunmola et Wyatt (06): Bayesian RL, have to check because I don't know what is it.

Walsh (06): They observe that "deciding what knowledge to transfer between environments can be boiled down to determining the correct state abstraction scheme for a set of source tasks and then applying this compaction to a target task", which is the idea of SRL and learning about the sensorimotor stream. Solve a set of MDPs, build abstractions from the solutions, extract relevant features, then apply the feature-based abstraction to a novel target task. They give theoritical guarantees that when the number of source tasks is large (relative to the difference between tasks) their type of abstraction are guaranteed to provide the optimal policy in a target task using Q-learning.

Lazaric (08): Learns a set of tasks with different reward functions using batch learning method Fitted Q-learning.

# 6/ Transferring task-invariant knowledge between tasks with differing state variables and actions

# 7/ Explicit mappings to transfer between different actions and state representations

# 8/ Learning task mappings

# 9/ Open questions

Go model-based for TL.

Look for Bayesian RL.

Train on a sequence of automatically generated source tasks.

Minor changes in R can lead to major changes in Q. How to solve that ? It breaks TL.

Decoupling benefits of TL to better understand it : better exploration and better internal state representation.

Meta-RL : learn the right learner.

Study the agent behaviour : agent space.

Negative transfer : decreased performance after having learned source task.

Get the similarity between two task can improve transfer strategies and better model the interactions between tasks.

How to construct a source task given a target task ? 

Theory in TL : 

- Guarantees about source task in helping target task.
- Correlate the amount of knowledge transferred (number of samples) with the improvement.
- Define what an optimla inter-task mapping is and demonstrate how transfer efficacy is impacted with the mapping.

Concept drift : MDP changes slowly and arbitrarily.

Determine the optimal amount of source task training to monimize the target task training time or total training time.

Account for scale difference between tasks.

Explore more in source in order to perform in target.

POMDPs, MMDPs, DEC-MDPs

No standard benchmark.



---------------

Final thoughts : 

The survey is very well written and very relevant to my work.

**To remember : Lazaric, Bayesian RL, no unique metric for TL so evaluate with number of metrics, clarify the setting of TL (we saw there are millions), go model-based, DQN nothing new, MTL included in TL, many good ideeas for each scenario of TL, SF for TL is nice because it has theory, no standard benchamarks.**
