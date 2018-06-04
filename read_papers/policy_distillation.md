Summary:

They propose to apply distillation to RL via policies. Pre-trained policies can be transferred to a smaller capacity policy (both being neural nets). 

They only show distillation for DQN, experimenting on Atari.

Method:
- Given a state, DQN outputs q-values for each action.
- So, in a buffer they store: inputs, outputs and game labels (for each different game). 

![](https://github.com/Caselles/paper_notes/blob/master/images/2.png)


- To perform distillation, they try 3 different losses: NLL, MSE, and KL (KL being the one used in the Hinton Distillation paper (I have a summary for that as well)). KL requires to optimize for the temperature Tau. In SL, they soften the teacher's outputs (high Tau), here they actually sharpen the outputs (low Tau). Their intuition behind that is: even if two q-values can be close, choosing the sub-optimal action can be crucially bad.

Experiments: 

Single game distillation: 

- KL is better than NLL and MSE. Expected but nice to have confirmed that. Sharpening the teacher's outputs is crucial (Tau = 0.001 (!)).
- For some games, the student is better than the teacher (which was also noticed for SL by Hinton).


Model-compression:

- Can distill into models that are 7% the number of parameters, and these models can't learn the task. Reasons for that are unclear. 

Multi-game distillation:

- Can distill 10 games into one large model (90% performance). Very nice. Some positive and negative transfer happen. Not really studied here.

Online distillation: 

- Can stabilize the training of the model by distilling everytime we get a new best model. For production, might be a good solution.



----------

Final thoughts:

This article is a demonstration that distillation can be applied to RL, via policies. They show that it's possible to 1) compress policies on single games in smaller models, 2) build one agent that can play 10 games and 3) you can have a model that learn in a more stable way using the non-stable learning model.

This is very useful for transfer. In P&C they show that you can distill and EWC to transfer without forgetting. This is very promising. 

----------

