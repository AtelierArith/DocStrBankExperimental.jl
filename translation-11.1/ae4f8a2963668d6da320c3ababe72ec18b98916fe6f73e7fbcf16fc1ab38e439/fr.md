```
prevpow(a, x)
```

Le plus grand `a^n` qui n'est pas supérieur à `x`, où `n` est un entier non négatif. `a` doit être supérieur à 1, et `x` ne doit pas être inférieur à 1.

Voir aussi [`nextpow`](@ref), [`isqrt`](@ref).

# Exemples

```jldoctest
julia> prevpow(2, 7)
4

julia> prevpow(2, 9)
8

julia> prevpow(5, 20)
5

julia> prevpow(4, 16)
16
```
