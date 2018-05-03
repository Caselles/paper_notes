Summary:

Setup: Markov Reward Process (MRP): MDP without actions. Define v_p general value functions on MRP. v_p is consistent with environment ssi v_p verifies Bellman equation of MRP (v=v_p)

Model:
- Four components: f, m, internal v, external v
- s = f(s) (can be recurrent)
- m is the MRP function estimate
- internal v is the remaining internal return
- external v is the estimate of external return : k-step and lambda-weighted
- k-step predictron: r_1 + gamma_1(r_2 +....+ gamma_k-1(r_k-1 + gamma_k.v_k)...))
- lambda-weighted predictron: combines many k-step preturns with weights, analogous to lambda-return in forward-view TD(lambda) algorithm. Can also be computed backward, just like the TD(lambda).

Learning updates: How to learn those components ?
- Update of the k-step preturn: the loss is MSE. 
- Same for lambda-predictron, but aggregated over individual preturns, and can use the weight in the udpate. Then can learn the weights lambda with eta.
- Summary: update theta (f,m,v) to make each k-step preturns g_k more similar to target g. update eta (w_k weights) to make lambda-preturn g_lambda more similar to target.
- Consistency updates: update theta so that g_k is more similar to g_lambda.

--------

Final thoughts:

Very hard to read. The idea is the following: the model in fully abstract contrary to model-based approaches, it need not to correspond to the real environment in any human understandable way, as long as its rolled-forward plans accurately predict outcomes. So it goes really against the approach we take in the phd.

--------

ICLR reject: https://openreview.net/forum?id=BkJsCIcgl (cas accepted to ICML after)
