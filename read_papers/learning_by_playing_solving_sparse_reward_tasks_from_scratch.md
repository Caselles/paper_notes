Résumé : https://deepmind.com/blog/learning-playing/. 

Idée : pour du RL sparse reward, surveiller pleins de tasks différentes, et optimiser pour celles-ci. Par cela, on peut occasionner des rewards rares, qui peuvent être l'objectif. Ainsi, on permets à l'algo d'etre data-efficient, car permets une exploration plus efficace. 

Comment ? DRL sur les rewards auxiliaires et reward principale + apprendre un scheduler qui choisit qu'est ce qui faut suivre comme police associée à une tâche pour maximiser la reward en tâche principale. Cf notes dans le papier. 
