```
@something(x...)
```

Version à court-circuit de [`something`](@ref).

# Exemples

```jldoctest
julia> f(x) = (println("f($x)"); nothing);

julia> a = 1;

julia> a = @something a f(2) f(3) error("Impossible de trouver une valeur par défaut pour `a`")
1

julia> b = nothing;

julia> b = @something b f(2) f(3) error("Impossible de trouver une valeur par défaut pour `b`")
f(2)
f(3)
ERREUR: Impossible de trouver une valeur par défaut pour `b`
[...]

julia> b = @something b f(2) f(3) Some(nothing)
f(2)
f(3)

julia> b === nothing
true
```

!!! compat "Julia 1.7"
    Ce macro est disponible depuis Julia 1.7.

