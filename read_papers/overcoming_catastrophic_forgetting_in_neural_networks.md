Summary:

Continual learning: being able to train a DNN on sequential tasks without catastrophic forgetting.

Propose Elastic Weight Consolidation algorithm, a general algorithm for avoiding catastrophic forgetting when the task are clearly delimited.

Idea: Slow down learning on weights that are important to other tasks. Neuroscience: reduce plasticity for vital synapses for other tasks (happens in the brain).

Works because there a lot of local optimas that are sufficiently good (over-parametrization is a good thing here).

They adopt a probabilistic prospective to optimizing neural nets: equivalent to finding the most probable parameters given the data (max p(D|theta) i.e max -Loss_D(theta) i.e min Loss_D(theta), logic).

-> log(p(theta|D)) = log(p(D|theta)) + log(p(theta)) - log(p(D)) (Bayes rule)

Key definition: log(p(D|theta)) is -Loss(theta), it's the proba of seeing this data given weight theta.

Then let's say we have trained parameters on D_a, and we have another dataset D_b:

-> log(p(theta|D)) = log(p(D_b|theta)) + log(p(theta|D_a)) - log(p(D_b|D_a)) (Bayes rule) 

We want to keep log(p(theta|D_a)) high while having log(p(D_b|theta)) high too. log(p(theta|D_a)) is intractable, they use a Laplace approximation.

They approximate the posterior as a Gaussian with mean theta_a (previous parameters) and a diagonal precision given by the diagonal of the Fischer information matrix F. F is equivalent to the second derivative of the loss near a minimum. Also, F is computable via first-order derivatives (so fast) and guaranteed to be positive semi-definite. 

So the end method is a regularization to the loss of B:

L(theta) = L_b(theta) + lambda/2 * sum_i(F_i(theta_i - theta_a,i)^2)

Discussion around what to do when you have three tasks are available in Huzsar's blog post. It is not clear what to do, because simply adding another separate penalty works in practice while you can derive a penalty for both of the previously learnt tasks. 

Experiments on Supervised Learning:

- permuted MNIST. EWC works at retaining knowledge (simple SGD/fine-tuning fails) and being able to learn new knowledge (L2 regularization fails).
- comparing overlap in Fischer information matrices show that knowledge is retained in input layers and shared in output layers. 


Experiments on Reinforcement Learning:

- 10 tasks Atari. Task changes every 2M steps. Forget Me Not model used to automatically detect changes in tasks. Double-DQN architecture with douple parameters than original paper. All configurations are specified in appendix. EWC penalty is applied by computing Fischer info every task switch, and added only to games that experienced at least 20M steps. Some parameters are game specific.
- Results: EWC retains knowledge. Still it is not on par with performance of a single DQN. Moving the parameters of the null space of F should not do anything but it does hurt performance, showing that we are over confident on which parameters are important or not. Still it behaves way better that random moving of the parameters.

-------

Final thoughts:

Very clear and nice idea, that works well on SL and not so well on RL. Many tricks for RL so there are ways to improve overcoming of catastrophic forgetting in RL. Also they do not investigate whether you can gain positive transfer from EWC. 

-------------

Huzsar blog post (summary + critic on the multiple penalties): http://www.inference.vc/comment-on-overcoming-catastrophic-forgetting-in-nns-are-multiple-penalties-needed-2/
