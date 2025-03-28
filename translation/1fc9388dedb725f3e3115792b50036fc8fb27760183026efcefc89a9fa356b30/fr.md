```
@spawnat p expr
```

Créez une fermeture autour d'une expression et exécutez la fermeture de manière asynchrone sur le processus `p`. Retournez un [`Future`](@ref) vers le résultat. Si `p` est le symbole littéral cité `:any`, alors le système choisira automatiquement un processeur à utiliser.

# Exemples

```julia-repl
julia> addprocs(3);

julia> f = @spawnat 2 myid()
Future(2, 1, 3, nothing)

julia> fetch(f)
2

julia> f = @spawnat :any myid()
Future(3, 1, 7, nothing)

julia> fetch(f)
3
```

!!! compat "Julia 1.3"
    L'argument `:any` est disponible depuis Julia 1.3.

