Summary:

They propose a way to form a skill repertoire with the continual learning of skills.

A first policy learns a first task, then a copy fine-tunes to a second task and both are distilled into a third policy. Then a fourth policy fine-tunes a third task and third and fourth are distilled, etc...

This figures sums it all up, experiments and concept included : 

![](https://github.com/Caselles/paper_notes/blob/master/images/3.png)

They give good insights on what works well with distillation.

----

Final thoughts:

From the reviews: "The authors propose an architecture that uses a manual curriculum and multi-task distillation to gain higher performance without forgetting. The paper is largely a smart composition of known methods, and it requires keeping data from all tasks to do the distillation, so it is not truly a scalable continual learning approach. This is a borderline paper."

This paper just shows again that distillation and fine-tuning as a transfer learning scheme are two mechanisms that work well in practice.

-------

ICLR 2018

Review: https://openreview.net/forum?id=B13njo1R-
