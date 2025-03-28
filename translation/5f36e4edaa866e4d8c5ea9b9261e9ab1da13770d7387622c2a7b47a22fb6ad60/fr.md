```
nfields(x) -> Int
```

Obtenez le nombre de champs dans l'objet donné.

# Exemples

```jldoctest
julia> a = 1//2;

julia> nfields(a)
2

julia> b = 1
1

julia> nfields(b)
0

julia> ex = ErrorException("J'ai fait une mauvaise chose");

julia> nfields(ex)
1
```

Dans ces exemples, `a` est un [`Rational`](@ref), qui a deux champs. `b` est un `Int`, qui est un type de bit primitif sans champs du tout. `ex` est un [`ErrorException`](@ref), qui a un champ.
