Summary: 

A deep RL method, augmented with memory (stacked LSTM) and auxiliary learning targets (depth and loop-closure prediction), for training agents to navigate within large and visually rich environments (frequently changing start and goal locations).

Navigation problems: 
- sparse rewards 
- need for memory (short for goal location, long for obstacles and boundaries)

Depth : predict 3D depth map (use low-res depth map to have better computational efficiency, classification or regression (classif works better))
Loop-closure : predict if state has already been visited within a local trajectory (binary loop label, has to be two states far way from each other)

Proposed architecture (pretty complex, overkill ?): 
- Stacked LSTMs A3C
- input to the CNN encoder
- reward as input to first LSTM
- velocity and last action as input to second LSTM
- depth prediction at the end of the CNN encoder
- depth and loop-closure prediction at the end of the stacked LSTMs

Experiments: evaluation on DeepMind Lab mazes 

Task : fruits, random goal and initial state, have to solve max maze in fixed amount of time

Their components allows for better performance.

They provide interesting ways of evaluating navigation skills and map knowledge of their agents. Useful monitoring and interpretation.

------------

Final thoughts: 

Related work section on Maze solving in RL is nice. Useful ways of evaluating navigation skills and map knowledge of their agents. Lots of computing power, seems really like a mess to implement.

------------

NIPS Oral: https://www.youtube.com/watch?v=5Rflbx8y7HY

Reviews:  https://openreview.net/forum?id=SJMGPrcle
