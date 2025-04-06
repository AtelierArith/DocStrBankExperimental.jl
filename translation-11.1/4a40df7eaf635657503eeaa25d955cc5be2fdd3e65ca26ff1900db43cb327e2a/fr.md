```
yieldto(t::Task, arg = nothing)
```

Bascule vers la tâche donnée. La première fois qu'une tâche est basculée, la fonction de la tâche est appelée sans arguments. Lors des bascules suivantes, `arg` est renvoyé de l'appel précédent de la tâche à `yieldto`. C'est un appel de bas niveau qui ne fait que basculer les tâches, sans tenir compte des états ou de la planification de quelque manière que ce soit. Son utilisation est déconseillée.
