```
@time expr
@time "description" expr
```

Une macro pour exécuter une expression, affichant le temps qu'il a fallu pour s'exécuter, le nombre d'allocations et le nombre total d'octets que son exécution a causé d'être alloués, avant de retourner la valeur de l'expression. Tout le temps passé à collecter les déchets (gc), à compiler du nouveau code ou à recompiler du code invalidé est affiché en pourcentage. Tout conflit de verrouillage où un [`ReentrantLock`](@ref) a dû attendre est affiché sous forme de compte.

Fournissez éventuellement une chaîne de description à imprimer avant le rapport de temps.

Dans certains cas, le système regardera à l'intérieur de l'expression `@time` et compilera une partie du code appelé avant que l'exécution de l'expression de niveau supérieur ne commence. Lorsque cela se produit, une partie du temps de compilation ne sera pas comptée. Pour inclure ce temps, vous pouvez exécuter `@time @eval ...`.

Voir aussi [`@showtime`](@ref), [`@timev`](@ref), [`@timed`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref), et [`@allocations`](@ref).

!!! note
    Pour des benchmarks plus sérieux, envisagez la macro `@btime` du package BenchmarkTools.jl qui, entre autres, évalue la fonction plusieurs fois afin de réduire le bruit.


!!! compat "Julia 1.8"
    L'option d'ajouter une description a été introduite dans Julia 1.8.

    Le temps de recompilation étant affiché séparément du temps de compilation a été introduit dans Julia 1.8


!!! compat "Julia 1.11"
    Le rapport de tout conflit de verrouillage a été ajouté dans Julia 1.11.


```julia-repl
julia> x = rand(10,10);

julia> @time x * x;
  0.606588 seconds (2.19 M allocations: 116.555 MiB, 3.75% gc time, 99.94% compilation time)

julia> @time x * x;
  0.000009 seconds (1 allocation: 896 bytes)

julia> @time begin
           sleep(0.3)
           1+1
       end
  0.301395 seconds (8 allocations: 336 bytes)
2

julia> @time "A one second sleep" sleep(1)
A one second sleep: 1.005750 seconds (5 allocations: 144 bytes)

julia> for loop in 1:3
            @time loop sleep(1)
        end
1: 1.006760 seconds (5 allocations: 144 bytes)
2: 1.001263 seconds (5 allocations: 144 bytes)
3: 1.003676 seconds (5 allocations: 144 bytes)
```
