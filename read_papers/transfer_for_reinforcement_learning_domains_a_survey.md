Summary : 

# 1/ Intro

Overview on RL and TL.
Approaches to solve problems of the PhD. 
Why is TL important ? 
How TL tasks are different ? 

# 2/ Evaluation

Full autonomous agent : 3 sub-problems. In reality people try to solve one of the 3, because it is hard.

1: Given a target task, select appropriate source task(s) from which to transfer
2: Learn how the source task(s) and target task are related
3: Effectively transfer knowledge from the source to the target

Total time vs target time ? Source task learning time should not be a sunk cost.

## 2.1/ Empirical transfer evaluation

Possible benefits of TL : Jump start, Asymptotic performance, Total reward, Transfer ratio, Time to threshold. Why not performance profile ? No unique metric, each is important.

Learning time = Sample complexity

Insights on problem with each metric.

Proposed metric : Ratio = (AUC with TL - AUC without TL)/(AUC without TL) >> Better, but still not scale invariant.

No comparison of TL algorithms between them in the literature.

## 2.2/ Dimensions of comparison







---------------

Final thoughts : 

The survey is very well written and very relevant to my work.
