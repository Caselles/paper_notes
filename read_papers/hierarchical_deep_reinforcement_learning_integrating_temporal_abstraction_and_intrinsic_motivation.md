Summary:

This paper considers a hierarchical approach to reinforcement learning, where a top-level controller selects subgoals for a low-level controller. 

The low-level controller is trained by DQN to select actions that maximise subgoal attainment for the specified subgoal. 

The high-level controller is trained by DQN to select subgoals as actions, which are then "executed" until completion, that maximise true reward. 

Promising results are demonstrated in the challenging Atari game Montezuma's Revenge, when using a mostly handcrafted set of subgoals. Trivial, but nice, results on a toy example. I like the toy example as a Proof of Concept.

--------

Final thoughts: 

Ideas are cool but experiments are vaguely described. Paper is vague about a lot of things. Since I like to really understand what I'm doing, I'm not really interested in pursuing this work.

--------

NIPS reviews: http://media.nips.cc/nipsbooks/nipspapers/paper_files/nips29/reviews/1826.html

Code (Lua...): https://github.com/mrkulk/hierarchical-deep-RL
