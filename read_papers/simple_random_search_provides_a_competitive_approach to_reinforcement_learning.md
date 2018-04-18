Summary : https://drive.google.com/file/d/1bTJVxJDN5b6FqyZ2fyvtZmUzvR1Rs5f3/view?usp=sharing

Instead of using all the bs DRL algorithms, they propose to use simple random search over the policy parameters, and they add 3 simple tricks to beat SOTA (in terms of sample complexity and performance) on practicly all MuJoCo tasks. 

The method is based on basic random search (BRS).

BRS : Set the policy Pi(x) = Mx, with M a n.p matrix (n is dimensionality of state space and p dimensionality of action space). Then search the parameters M that yields the policy that yields the most reward. Sample k n.p-dimensional gaussian (deltas). For each sample, run both policies: M+nu.delta and M-nu.delta. Update according to the best direction, the one that gave the most reward. Simple as that.

Hyperparameters : nu, step size, n.

The three tricks they add : 

- Scale the update by the std of rewards accumulated.
- Normalize the states.
- Use only b best directions (the one that gave the most reward).

Experiments show that it obliterates other method on MuJoCo. Then the authors proceed to expose every problem in the DRL community, which I agree with. 

LQR : ARS does not particulary well on a challenging instance of LQR. Means that there is a lot of room for improvement in model-free RL methods. All the DRL BS would do poorly on this instance of LQR they say, they do not show it though (why? too hard to do I guess).

--------------

Final thoughts : 

For me this is a groundbreaking paper, since it solves every problem DRL has on MuJoCo : policy interpretability, sample complexity, debugging problems, variance over runs, performance. 

This allows for so much improvement: 

- Policy is linear. So each policy is a set of n.p parameters, which is ridiculously small. Plus it trains in no time. This can certainly be abused for TL.
- If the action state is discrete, how can you use ARS ? Regression for multinomial variables ? Cf carnet. Possiility of having a stochastic policy. 
- If the state space is made of RGB images (or n is large), how can you use ARS ? Use features of SRL ? 
- Policy interpretability ? Policy is linear so we could extract knowledge from it.

----------------

Argmin blog article : http://www.argmin.net/2018/03/20/mujocoloco/

Code : https://github.com/modestyachts/ARS
