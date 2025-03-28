```
nextpow(a, x)
```

Le plus petit `a^n` qui n'est pas inférieur à `x`, où `n` est un entier non négatif. `a` doit être supérieur à 1, et `x` doit être supérieur à 0.

Voir aussi [`prevpow`](@ref).

# Exemples

```jldoctest
julia> nextpow(2, 7)
8

julia> nextpow(2, 9)
16

julia> nextpow(5, 20)
25

julia> nextpow(4, 16)
16
```
