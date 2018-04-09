Summary  :

Core idea : "It is however possible to draw another conclusion, namely that this sequence of actions would be successful if the net had been placed further to the right. In this paper we introduce a technique calledHindsight Experience Replay (HER) which allows the algorithm to perform exactly this kind of reasoning and can be combined with any off-policy RL algorithm."

See algorithm 1, very clear what HER does.

Makes use of UVFA (so goal space) for off-policy algo such as DQN, DDPG, NAF, SDQN. Goal space is, unfortunately, uses the same space that the state space. >> No complicated goal so no complicated behaviour <<

Shaped reward function does not perform well. The important problem seem to be sparse-reward RL rather than designing reward functions that make algorithms work well.

I have some code that implements the method. Seem to work, so I'll keep this method in mind for future expriments.

--------------

Final words : 

Simple way to make learning more sample-efficient. The core idea is cool. It would be nice to have a theoritical analysis of the method (seems possible in a simple case). I have code for the method. 

---------------

Summary : https://becominghuman.ai/learning-from-mistakes-with-hindsight-experience-replay-547fce2b3305

Reviews : https://media.nips.cc/nipsbooks/nipspapers/paper_files/nips30/reviews/2595.html
