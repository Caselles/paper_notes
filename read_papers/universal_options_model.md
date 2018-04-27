Summary :

Problem : Planning over options are tied to one reward that you need to estimate. Once the reward change, have to restart from sctrach. How to generalize to mutiple rewards scenario ? 

Option framework : 
- Option = policy + continuation function (maps states to termination probability)
- Option model = Option return(= expected return of trying an option (random termination)) + discounted sum of probabilities of termination (discounted sum over k of proba of terminating at state s' starting from s, for k number of timesteps between s and s')
- SMDP: MDP that allows mult-step transitions between states. An option policy (= high-level policy) gives rise to a MDP policy after flattening it. Bellman's equation holds if actions are options, return are option returns, and transitions proba are terminal distributions.

Universal Option Models (things get shady...): Goal is to make an option model that is reward-independent. 
- You can write the value function in terms of discounted occupancy function, which is essentially the Successor Representation. It means that if we have the discounted occupancy function of a policy (which you can get with a forward model), you just have to multiply it by a particular reward weight vector to get the value function. (why don't they cite Dayan's SR paper?)
- So the generalization writes the discounted state occupancy function u_o of an option o. Then you can write the return of the option using this u_o.
- I don't understand Theorem 1, it seems that it is trivial given Eq(2).

UOMs with Linear Function Approximation (things get shadier):
- Assume that you have a n-dimensional map (like in State Representation Learning) phi from states to R^n
- Let the value function be a linear combination of phi (hmmmm)
- Then you can estimate the TD(0) error with respect to a particular reward as solution to Bellman's equation
- If there is no gamma, then the solution to Bellman's equation is the least squares approximation to the immediate rewards
- In fact, we define f as the least squares approximation to the immediate rewards of the option return
- Then they define the linear UOM, which is a pair of matrices (U_o, M_o). 
- U_o solve for a system of linear Bellman equations. It is backward compatible to the definition of UOMs in the tabular case. 
- Theorem 2: For a specific reward, its TD(0) error is the least squares approximation f w.r.t R, dot product with (U_o.phi). It means that if you know U, you just have to do a least squares approximation, much simpler than a TD fixed-point equation.
- M_o 




---------

Final thoughts : 


---------

Can't find supplementary material ...!
