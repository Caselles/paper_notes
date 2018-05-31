Summary:

One of the first paper about distillation with neural nets.

The idea is the following: using a teacher network's outputs as soft targets for a student network.

Intuition: A BMW is close to a truck, and very different from a carrot. This valuable information is not present in hard labels and present in soft labels provided by a pretrained teacher.

Other intuition: If several pretrained teachers do not agree on the label of a sample x then you know which classes the label is close to.

They define distillation by not using directly the output of a softmax (which is typically the case) or the logit (which is the output of the network before softmax), but a version of the ouput with a higher temperature softmax, to soften the labels. Hence the outputs are not extreme (like 0.999999, 0.000001), but softer (like 0.8, 0.2).

They show that matching logits is a special case of distillation with very high temperatures compared to the logits. They study the tradeoff between high and low temperature empirically. If the capacity of the student is low, they show that low temperature is better.

Experiments: 

With their various SL experiments, they show: 

- A student with small capacity can have same (even better) accuracy that a high capacity teacher.
- A student can learn without even seeing whole parts of the dataset (missing examples from labels, and/or seeing only 3% of the dataset).




---------

Final thoughts:

Distillation works, there has been lots of follow-up to this. Temperature is important. See Policy Distillation for RL experiments.

------------

