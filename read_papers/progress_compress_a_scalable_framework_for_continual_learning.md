Summary:

The general idea is to create a scalable framework for continual learning. Which means, the system must fulfill these criteria:

- No catastrophic forgetting
- Positive forward transfer (faster learning and/or better final performance)
- Scalable w.r.t the number of tasks
- Positive backward transfer : immediate better performance on previous task after learning new task
- No need for task labels, should be able to detect changes in tasks automatically

For that, they propose the Progress & Compress framework (P&C), which combines distillation (for compression), a modified EWC (for avoiding catastrophic forgetting) and lateral connections of Progressive Nets (for reuse of past knowledge while learning a new task).

Task here refer to either a SL task, or a RL task. 

Description of the method:

- Two alternating stages: Progress (day, learning a new task) and Compress (night, consolidate knowledge acquired)
- Hence, two modules: active column (AC) and knowledge base (KB). Outputs are class probabilities for SL and policies/values for RL.
- First stage: Progress. The AC learn the new task, with the help of the KB using lateral connections, with the same mechanism as in Progressive nets (e.g. lateral connections with adaptators weights for a suitable scaling). 
- Second stage: Compress. Newly learnt behaviour is consolidate into the KB via distillation, and the KB is protected from catastrophic forgetting using EWC. 
- They use KL for distillation and do not discuss the temperature issue.  
- They use what they call Online EWC, which a modified version of EWC. EWC is straightforward as long as you have two tasks. When you have more, then there are various approximation choices you can make to create the loss function of the ith task. First one is adding all previous penalty terms from previous tasks, which does not scale well. Otherwise, as pointed by Ferenc Huzsar: using the sum of Fischer info matrix and only the last optimal parameter, while already being an approximation (in theory you would have to recompute the Fisher matrix for all task everytime you have a new MAP parameter (the optimal theta after learning a task), which is indeed infeasible), does not yield good results because it does not constrain the new parameters to be close to parameters that are optimal for old tasks, given the approximation. So they propose to use the latter version but with a decay gamma over Fisher matrices, which found to work well empirically.

Experiments:

They experiment on SL with Omniglot and on RL with 6 Atari games and navigation tasks in DeepMind Lab (I guess).

Resilience against catastrophic forgetting:

- Ok on Omniglot even after 49 tasks. 

Forward transfer: 

- Positive on navigation tasks and Atari. You should randomly initialize the weights of the AC, otherwise you lose transfer.

Overall performance:

- Weird figures for RL. Overall performance is better for P&C, but the shape of the curves are weird. Why is it doing that ? It seems that training longer hurts performance. No comment on that it seems.




P.S: Related work section is a gold mine, I would like to thank the authors. This paper is a very good gateway to continual learning.

-------

Final thoughts:

The framework nicely blends distillation, progressive nets ideas and EWC. Nice insights too. Adding tasks where the agent need memory could be interesting. 

------

ICML 2018
