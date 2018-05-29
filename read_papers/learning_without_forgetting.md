Summary:

Propose a solution to continual learning with neural nets while avoiding catastrophic forgetting. 

It is a computer vision paper so they evaluate on sequential tasks involving ImageNet, Places365, CUB, VOC, Scenes.

They propose a training procedure and test it in various experiments.

Architecture + procedure:

- Add just an output layer for each tasks, randomly initalized. Record the outputs for each image of the new task. Then fine-tune the whole thing on the new task images by using the recorded outputs as targets for the previous task outputs. For the new output, train normally. They use weight decay as regularization. 
- The procedure is IMO not very clear.

Experiments:

- Most of the time, better results than fine-tuning (!).
- Most of the time, LwF does not forget what it has learn on previous tasks.

-------

Final thoughts:

Nice results, another choice for continual learning. Have to prove that it works for RL though, since it is quite different than SL. Not sure how to extend the "record" stuff. This method seems really tight to batch learning and not online learning.



----------

Code (authors, matlab): https://github.com/lizhitwo/LearningWithoutForgetting

