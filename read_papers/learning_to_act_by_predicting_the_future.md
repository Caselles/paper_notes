Summary : 

Uses supervised learning to learn to predict future measurements for each action. Goals are defined in terms of measurements. Selecting actions in order to respect goal yields learning of behaviors that allowed the method to win the VizDoom competition.

-----------

Final Thoughts : 

Love this. Sensorimotor prediction that seems to yield stable behaviour learning in complex environments. One idea would be to couple DFP with SRL and use state features as measurements.

------------


Summary: https://blog.acolyer.org/2017/05/12/learning-to-act-by-predicting-the-future/

OpenReview : https://openreview.net/forum?id=rJLS7qKel

Simple Keras code for VizDoom, seem to work, plus blog article with summary and hindsights: https://flyyufelix.github.io/2017/11/17/direct-future-prediction.html


**N.B : the second section of the paper ("Background") gives an interesting overview of sensorimotor prediction, as well as an overview on SL vs RL for learning how to act by interacting with an environment.** 
