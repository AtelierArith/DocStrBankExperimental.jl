```
cmp(x,y)
```

Retourne -1, 0 ou 1 selon que `x` est inférieur, égal ou supérieur à `y`, respectivement. Utilise l'ordre total implémenté par `isless`.

# Exemples

```jldoctest
julia> cmp(1, 2)
-1

julia> cmp(2, 1)
1

julia> cmp(2+im, 3-im)
ERROR: MethodError: no method matching isless(::Complex{Int64}, ::Complex{Int64})
[...]
```
