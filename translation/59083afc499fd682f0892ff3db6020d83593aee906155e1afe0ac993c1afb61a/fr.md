```
TaskLocalRNG
```

Le `TaskLocalRNG` a un état qui est local à sa tâche, et non à son thread. Il est initialisé lors de la création de la tâche, à partir de l'état de sa tâche parente, mais sans faire avancer l'état du RNG de la tâche parente.

Comme avantage, le `TaskLocalRNG` est assez rapide et permet des simulations multithreadées reproductibles (en évitant les conditions de course), indépendamment des décisions du planificateur. Tant que le nombre de threads n'est pas utilisé pour prendre des décisions sur la création de tâches, les résultats de simulation sont également indépendants du nombre de threads / CPU disponibles. Le flux aléatoire ne devrait pas dépendre des spécificités matérielles, jusqu'à l'endianness et éventuellement la taille des mots.

Utiliser ou initialiser le RNG de toute autre tâche que celle retournée par `current_task()` est un comportement indéfini : cela fonctionnera la plupart du temps, et peut parfois échouer silencieusement.

Lors de l'initialisation de `TaskLocalRNG()` avec [`seed!`](@ref), la graine passée, le cas échéant, peut être n'importe quel entier.

!!! compat "Julia 1.11"
    L'initialisation de `TaskLocalRNG()` avec une graine entière négative nécessite au moins Julia 1.11.


!!! compat "Julia 1.10"
    La création de tâches n'avance plus l'état du RNG de la tâche parente depuis Julia 1.10.

