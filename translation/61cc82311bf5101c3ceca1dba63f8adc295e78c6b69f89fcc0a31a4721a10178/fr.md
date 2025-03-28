```
Threads.@threads [schedule] for ... end
```

Une macro pour exécuter une boucle `for` en parallèle. L'espace d'itération est distribué à des tâches à grain grossier. Cette politique peut être spécifiée par l'argument `schedule`. L'exécution de la boucle attend l'évaluation de toutes les itérations.

Voir aussi : [`@spawn`](@ref Threads.@spawn) et `pmap` dans [`Distributed`](@ref man-distributed).

# Aide étendue

## Sémantique

À moins que des garanties plus fortes ne soient spécifiées par l'option de planification, la boucle exécutée par la macro `@threads` a les sémantiques suivantes.

La macro `@threads` exécute le corps de la boucle dans un ordre non spécifié et potentiellement de manière concurrente. Elle ne spécifie pas les affectations exactes des tâches et des threads de travail. Les affectations peuvent être différentes pour chaque exécution. Le code du corps de la boucle (y compris tout code appelé de manière transitive à partir de celui-ci) ne doit pas faire d'hypothèses sur la distribution des itérations aux tâches ou sur le thread de travail dans lequel elles sont exécutées. Le corps de la boucle pour chaque itération doit être capable de progresser indépendamment des autres itérations et être exempt de courses de données. En tant que tel, des synchronisations invalides entre les itérations peuvent entraîner un blocage, tandis que des accès mémoire non synchronisés peuvent entraîner un comportement indéfini.

Par exemple, les conditions ci-dessus impliquent que :

  * Un verrou pris dans une itération *doit* être libéré dans la même itération.
  * Communiquer entre les itérations en utilisant des primitives de blocage comme les `Channel`s est incorrect.
  * Écrire uniquement dans des emplacements non partagés entre les itérations (à moins qu'un verrou ou une opération atomique ne soit utilisée).
  * À moins que le plan `:static` ne soit utilisé, la valeur de [`threadid()`](@ref Threads.threadid) peut changer même au sein d'une seule itération. Voir [`Migration de tâche`](@ref man-task-migration).

## Planificateurs

Sans l'argument de planification, la planification exacte n'est pas spécifiée et varie selon les versions de Julia. Actuellement, `:dynamic` est utilisé lorsque le planificateur n'est pas spécifié.

!!! compat "Julia 1.5"
    L'argument `schedule` est disponible depuis Julia 1.5.


### `:dynamic` (par défaut)

Le planificateur `:dynamic` exécute les itérations dynamiquement sur les threads de travail disponibles. L'implémentation actuelle suppose que la charge de travail pour chaque itération est uniforme. Cependant, cette hypothèse peut être supprimée à l'avenir.

Cette option de planification est simplement un indice pour le mécanisme d'exécution sous-jacent. Cependant, quelques propriétés peuvent être attendues. Le nombre de `Task`s utilisées par le planificateur `:dynamic` est limité par un petit multiple constant du nombre de threads de travail disponibles ([`Threads.threadpoolsize()`](@ref)). Chaque tâche traite des régions contiguës de l'espace d'itération. Ainsi, `@threads :dynamic for x in xs; f(x); end` est généralement plus efficace que `@sync for x in xs; @spawn f(x); end` si `length(xs)` est significativement plus grand que le nombre de threads de travail et que le temps d'exécution de `f(x)` est relativement plus petit que le coût de création et de synchronisation d'une tâche (généralement moins de 10 microsecondes).

!!! compat "Julia 1.8"
    L'option `:dynamic` pour l'argument `schedule` est disponible et par défaut depuis Julia 1.8.


### `:greedy`

Le planificateur `:greedy` crée jusqu'à [`Threads.threadpoolsize()`](@ref) tâches, chacune travaillant de manière avide sur les valeurs itérées données au fur et à mesure qu'elles sont produites. Dès qu'une tâche termine son travail, elle prend la valeur suivante de l'itérateur. Le travail effectué par une tâche individuelle n'est pas nécessairement sur des valeurs contiguës de l'itérateur. L'itérateur donné peut produire des valeurs indéfiniment, seule l'interface de l'itérateur est requise (pas d'indexation).

Cette option de planification est généralement un bon choix si la charge de travail des itérations individuelles n'est pas uniforme/a une grande dispersion.

!!! compat "Julia 1.11"
    L'option `:greedy` pour l'argument `schedule` est disponible depuis Julia 1.11.


### `:static`

Le planificateur `:static` crée une tâche par thread et divise les itérations également entre elles, assignant chaque tâche spécifiquement à chaque thread. En particulier, la valeur de [`threadid()`](@ref Threads.threadid) est garantie d'être constante au sein d'une itération. Spécifier `:static` est une erreur si utilisé à l'intérieur d'une autre boucle `@threads` ou depuis un thread autre que 1.

!!! note
    La planification `:static` existe pour soutenir la transition de code écrit avant Julia 1.3. Dans les fonctions de bibliothèque nouvellement écrites, la planification `:static` est déconseillée car les fonctions utilisant cette option ne peuvent pas être appelées depuis des threads de travail arbitraires.


## Exemples

Pour illustrer les différentes stratégies de planification, considérons la fonction suivante `busywait` contenant une boucle temporelle non cédante qui s'exécute pendant un certain nombre de secondes.

```julia-repl
julia> function busywait(seconds)
            tstart = time_ns()
            while (time_ns() - tstart) / 1e9 < seconds
            end
        end

julia> @time begin
            Threads.@spawn busywait(5)
            Threads.@threads :static for i in 1:Threads.threadpoolsize()
                busywait(1)
            end
        end
6.003001 secondes (16.33 k allocations: 899.255 KiB, 0.25% temps de compilation)

julia> @time begin
            Threads.@spawn busywait(5)
            Threads.@threads :dynamic for i in 1:Threads.threadpoolsize()
                busywait(1)
            end
        end
2.012056 secondes (16.05 k allocations: 883.919 KiB, 0.66% temps de compilation)
```

L'exemple `:dynamic` prend 2 secondes car l'un des threads non occupés est capable d'exécuter deux des itérations de 1 seconde pour compléter la boucle for. ```
