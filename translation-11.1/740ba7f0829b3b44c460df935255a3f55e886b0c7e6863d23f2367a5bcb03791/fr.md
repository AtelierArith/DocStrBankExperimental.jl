```
@elapsed
```

Une macro pour évaluer une expression, en ignorant la valeur résultante, et en retournant plutôt le nombre de secondes qu'il a fallu pour s'exécuter sous forme de nombre à virgule flottante.

Dans certains cas, le système regardera à l'intérieur de l'expression `@elapsed` et compilera une partie du code appelé avant que l'exécution de l'expression de niveau supérieur ne commence. Lorsque cela se produit, un certain temps de compilation ne sera pas compté. Pour inclure ce temps, vous pouvez exécuter `@elapsed @eval ...`.

Voir aussi [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref), [`@allocated`](@ref), et [`@allocations`](@ref).

```julia-repl
julia> @elapsed sleep(0.3)
0.301391426
```
