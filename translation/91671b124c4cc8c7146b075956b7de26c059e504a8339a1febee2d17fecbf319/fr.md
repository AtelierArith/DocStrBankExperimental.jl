```
@spawn expr
```

Créez une fermeture autour d'une expression et exécutez-la sur un processus choisi automatiquement, renvoyant un [`Future`](@ref) vers le résultat. Ce macro est obsolète ; `@spawnat :any expr` doit être utilisé à la place.

# Exemples

```julia-repl
julia> addprocs(3);

julia> f = @spawn myid()
Future(2, 1, 5, nothing)

julia> fetch(f)
2

julia> f = @spawn myid()
Future(3, 1, 7, nothing)

julia> fetch(f)
3
```

!!! compat "Julia 1.3"
    À partir de Julia 1.3, ce macro est obsolète. Utilisez `@spawnat :any` à la place.

