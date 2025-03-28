```
strides(A)
```

Renvoie un tuple des pas de mémoire dans chaque dimension.

Voir aussi : [`stride`](@ref).

# Exemples

```jldoctest
julia> A = fill(1, (3,4,5));

julia> strides(A)
(1, 3, 12)
```
