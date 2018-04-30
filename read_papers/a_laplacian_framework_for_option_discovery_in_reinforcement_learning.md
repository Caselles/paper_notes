Summary:

They use options framework (check options overview by Precup if not familiar), with the simplification that you don't have termination functions but termination states.

They tackle automatic option discovery. 

Representation learning: Proto-value functions is a way to learn representations in an MDP. Create graph of transitions from transition matrix. Take adjacency matrix, then take Laplacian. Eigendecomposition of Laplacian, and then eigenvectors are used to estimate value function. It is a basis of the MDP. Capture goemetry of environment, reward-independent. 

Soooo... discover options with PVF ! Really natural idea.

Idea: 

- Define intrinsic reward function r_i by using PVFs, called eigenpurpose. They use the difference in PVF between states as rewards. Key idea.
- Define MDP using the intrinsic reward function and the "terminate" action in order to let the agent quit the option.
- You can use classic RL tools on MDPs such as value function evaluation. An optimal policy for the MDP is the eigenbehaviour. 
- To terminate: at the state where you cannot do better, just terminate. They provide a Theorem to prove that this condition is always verified.

So they autonomous option discovery.

Does it works ? 
- Discovered options:
Seems logical, and purpose driven.

- Improvements in exploration:
When you use PVF options, you get more efficient exploration of state space compared to primitive actions.
Bottlenecks can be bad for learning. 

- Improvements in performance:
Yes you can learn faster in grid-world.

What do you do if you cannot enumerate states ? 
- We need the graph: sample-based method. Random walk in the graph. In the limit it converges. You need a discrete representation...
- Function approximation: use it. 

Proposed work: 
- Theoretical results on the role of options in RL 
- Better representation learning
- Incremental learning of this method, end-to-end (SVD for ex is not incremental). How to find the right number of options ? 



--------------

Final thoughts:

Natural idea. Use PVF to have representation of your MDP, and then use these representations to define options. Does not seem scalable, but this group of researchers are trying to find theoretically sound stuff. So I like this work.

------------ 

Video of first author: https://vimeo.com/220484541
