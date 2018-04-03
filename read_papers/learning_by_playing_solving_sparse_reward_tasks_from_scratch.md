Summary by DeepMind (a bit pretentious imo) : https://deepmind.com/blog/learning-playing/. 

--------------------------------------

My summary : 

SAC-X is based on the idea that to learn complex tasks from scratch, an agent has to learn to explore and master a set of basic skills first. For sparse reward RL, the idea is to consider lots of different tasks, and optimize for all of them. In this process, rare rewards of the real objective task can occur. Hence, the exploration process in more clever than random, which allows for a more data-efficient algorithm.

How ? Deep RL on auxiliary rewards and main objective reward, and learn a scheduler which choses which policy associated to a task to follow in order to maximize the main objective reward.

-----------------------------------------------

Final words : **Interesting way of using auxiliary task to optimize the exploration**. 
