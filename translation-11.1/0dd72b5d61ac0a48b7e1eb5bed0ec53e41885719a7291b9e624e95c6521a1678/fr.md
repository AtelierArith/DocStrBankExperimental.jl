```
Threads.foreach(f, channel::Channel;
                schedule::Threads.AbstractSchedule=Threads.FairSchedule(),
                ntasks=Threads.threadpoolsize())
```

Semblable à `foreach(f, channel)`, mais l'itération sur `channel` et les appels à `f` sont répartis sur `ntasks` tâches lancées par `Threads.@spawn`. Cette fonction attend que toutes les tâches lancées en interne soient terminées avant de retourner.

Si `schedule isa FairSchedule`, `Threads.foreach` tentera de lancer des tâches de manière à permettre à l'ordonnanceur de Julia de mieux équilibrer la charge de travail entre les threads. Cette approche a généralement un coût par élément plus élevé, mais peut mieux performer que `StaticSchedule` en concurrence avec d'autres charges de travail multithreadées.

Si `schedule isa StaticSchedule`, `Threads.foreach` lancera des tâches d'une manière qui entraîne un coût par élément inférieur à celui de `FairSchedule`, mais qui est moins propice à l'équilibrage de la charge. Cette approche peut donc être plus adaptée aux charges de travail uniformes et de petite taille, mais peut moins bien performer que `FairSchedule` en concurrence avec d'autres charges de travail multithreadées.

# Exemples

```julia-repl
julia> n = 20

julia> c = Channel{Int}(ch -> foreach(i -> put!(ch, i), 1:n), 1)

julia> d = Channel{Int}(n) do ch
           f = i -> put!(ch, i^2)
           Threads.foreach(f, c)
       end

julia> collect(d)
collect(d) = [1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361, 400]
```

!!! compat "Julia 1.6"
    Cette fonction nécessite Julia 1.6 ou une version ultérieure.

