Summary : 



---------------

Final thoughts : 

The core idea is to remove the expectations from the Bellman equation. And then do the same thing that is done in RL with expectation.

They provide a policy evaluation setting : For the Bellman Equation, we have the infinity norm that allows contraction in order to approximate the expectation of the Q function. Here, we need another norm. KL and total variation does not work. They use the maximal Wasserstein metric to obtain contraction. 

They provide control : they show we do not have control in fact.

Algorithm C51 : 

1: Sample a transition
2: Compute target
3: Project onto approximation support (51 bins distribution)
4: Minimize KL divergence between target approximation and candidate approximation.

C51 surprisingly works very well (performance and speed), they don't know why. Yay... 

Why having results with the maximal W norm and then not being able to use it in the algo ? Disappointing. 

---------------

Final thoughts : 

Seems hard to implement. Seems like WIP. Have to keep an eye on research in Distributional RL, new results might come. Have to check Cramer distance solution to biased Wasserstein gradients.

---------------

Video of main author : https://www.youtube.com/watch?v=ba_l8IKoMvU

Blog post Deepmind : https://deepmind.com/blog/going-beyond-average-reinforcement-learning/

Code : https://github.com/Kiwoo/distributional_perspective_on_RL
