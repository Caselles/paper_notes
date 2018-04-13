Summary: 

The model proposed has a large world model and a small controller. The world model proposed tries to predict the future based on its actions and state (image). The small controller tries to find a policy to solve a task.

Hence there a 3 components : 

- V(ision): a VAE that learns a latent space Z of images.
- M(emory): a RNN that takes as input z (in Z) and tries to predict the future by predicting the distribution z' over the next states, by using a MDN-RNN. Will have to see how it works this MDN-RNN.
- C(ontroller): Simple linear policy. It tries to maximize the cumulative reward, and has z (the image) and h (the hiddent state of the RNN, which roughly encodes for "what's going on" or "which course of action is taken right now") as inputs. Logic !

def rollout(controller):
  ''' env, rnn, vae are '''
  ''' global variables  '''
  obs = env.reset()
  h = rnn.initial_state()
  done = False
  cumulative_reward = 0
  while not done:
    z = vae.encode(obs)
    a = controller.action([z, h])
    obs, reward, done = env.step(a)
    cumulative_reward += reward
    h = rnn.forward([a, z, h])
  return cumulative_reward
  
This pseudo-code explains how the model is trained. Why don't we have such pseudo-code in every paper ? It's so clear.
  
C is very small so you can learn very quickly and since we know DRL or ES is a pain in the ass it is a very useful thing. All the complexity is put in the models that we know are easier to train (RNN, VAE). Great idea.

Experiments are really impressing. Only 800 parameters for the policy and it solves a yet to be solved gym env.

---------

Final thoughts:

Waw the online article is amazing. So clear, even if the paper is quite complex. I love this stuff and want to do it too for my research. 

---------

"Blog post" paper: https://worldmodels.github.io/

Other summary: https://github.com/abhshkdz/papers/blob/master/reviews/world-models.md
