```
iseven(x::Number) -> Bool
```

Retourne `true` si `x` est un entier pair (c'est-à-dire un entier divisible par 2), et `false` sinon.

!!! compat "Julia 1.7"
    Les arguments non-`Integer` nécessitent Julia 1.7 ou version ultérieure.


# Exemples

```jldoctest
julia> iseven(9)
false

julia> iseven(10)
true
```
