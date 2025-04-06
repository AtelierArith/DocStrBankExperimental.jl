```
ndigits(n::Integer; base::Integer=10, pad::Integer=1)
```

Calcule le nombre de chiffres dans l'entier `n` écrit en base `base` (la `base` ne doit pas être dans `[-1, 0, 1]`), éventuellement complété par des zéros jusqu'à une taille spécifiée (le résultat ne sera jamais inférieur à `pad`).

Voir aussi [`digits`](@ref), [`count_ones`](@ref).

# Exemples

```jldoctest
julia> ndigits(0)
1

julia> ndigits(12345)
5

julia> ndigits(1022, base=16)
3

julia> string(1022, base=16)
"3fe"

julia> ndigits(123, pad=5)
5

julia> ndigits(-123)
3
```
