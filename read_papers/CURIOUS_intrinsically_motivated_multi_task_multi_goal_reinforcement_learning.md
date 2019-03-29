Summary:

Multi-task multi-goal RL. Each task can be parametrized by a goal.

For RL, they extend UVFA to E-UVFA by concatenating state, goal and task. The policy is monolithic, conditioned by task and goals.

In order to select which task to perform and when, they use a Learning Progress metric. The chosen task is the one that give the most absolute learning progress, and exploration of tasks is still maintained with an epsilon-greedy approach to task selection.

They perform ablation studies to justify the proposed approached compared to simpler baselines. CURIOUS and E-UVFA provide better robustness to distraction and forgetting, as they help recover faster, remember better, and achieve overall faster learning.

-----------

Final thoughts: 

Nice job Cédric! :p I like that the approach is fully autonomous (the agent select what it learns). On the down side it seems a bit complicated to implement.


