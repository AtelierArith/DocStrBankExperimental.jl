```
checkbounds(Bool, A, I...)
```

Retourne `true` si les indices spécifiés `I` sont dans les limites pour le tableau donné `A`. Les sous-types de `AbstractArray` devraient spécialiser cette méthode s'ils ont besoin de fournir des comportements de vérification des limites personnalisés ; cependant, dans de nombreux cas, on peut se fier aux indices de `A` et à [`checkindex`](@ref).

Voir aussi [`checkindex`](@ref).

# Exemples

```jldoctest
julia> A = rand(3, 3);

julia> checkbounds(Bool, A, 2)
true

julia> checkbounds(Bool, A, 3, 4)
false

julia> checkbounds(Bool, A, 1:3)
true

julia> checkbounds(Bool, A, 1:3, 2:4)
false
```
