```
isodd(x::Number) -> Bool
```

Retourne `true` si `x` est un entier impair (c'est-à-dire un entier non divisible par 2), et `false` sinon.

!!! compat "Julia 1.7"
    Les arguments non-`Integer` nécessitent Julia 1.7 ou une version ultérieure.


# Exemples

```jldoctest
julia> isodd(9)
true

julia> isodd(10)
false
```
