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

Sherstov and Stone (05): Rather than reasoning over the proba of reaching a given state after an action, the learner reasons over the actions' effect, or outcome. States













---------------

Final thoughts : 

The survey is very well written and very relevant to my work.
