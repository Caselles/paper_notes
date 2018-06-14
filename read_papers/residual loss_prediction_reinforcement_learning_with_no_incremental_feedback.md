Summary :

The goal is to learn a denser reward function from a sparse one, a long standing goal in RL. They propose RESLOPE.

RESLOPE operates as a reduction to contextual bandits, using its internal learned loss representation to solve the credit assignment problem, and a contextual bandit oracle to trade-off exploration and exploitation. 

The contextual bandit is in turn reduced to a cost-sensitive classification, which specifies the cost for each actions given an input x. They try three different methods for this classification.

Then the exploration/exploitation dilemma is handled by exploration strategies, they try three different methods here too.

The theoretical guarantees for RESLOPE are : If the CB algo is no-regret (e.g. asymptotically), then RESLOPE is no-regret. So they rely on having good CB algorithms. Why no guarantees for the method they actually tried here ? Are there any guarantees for a reduction of CB to cost-sensitive classification ? I don't know.

Experiments :

They experiment on Bandit Structured Prediction problems and RL problems (cartpole, blackjack, hex, gridworld). I did not check the BSP results.

Rl results are quite disappointing: RESLOPE is no better than A2C or PPO. Still, it works well so this is a good proof of concept. 

----------------

Final thoughts : 

Too bad it does not work very well in practice. In Rl experiments, RESLOPE has similar results to PPO and A2C. 

The general idea of learning a denser reward function from a sparse one is important. The reduction of the problem to a contextual bandit problem to enjoy theoretical regret guarantees is very nice. 

I like this work but I have trouble evaluating how useful it can really be, since the experiment results are not that impressive. 

It is disappointing that the theoretical guarantees seem to apply on a case that does not well in practice (single deviation), while it is unclear is the guarantees apply for the case that does well in practice. Because beta = 0 in RL.

I hope there will be follow-ups to this paper because it is very nice to have theoretical guarantees here. The problem is better understood.

Disclaimer: I don't think I entirely understood the paper. It is hard to follow as a reviewer said.




-----------

ICLR 2018

Reviews : https://openreview.net/forum?id=HJNMYceCW
