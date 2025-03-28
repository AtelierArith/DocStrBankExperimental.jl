```
>(x, y)
```

Opérateur de comparaison supérieur à. Se rabat sur `y < x`.

# Implémentation

En général, les nouveaux types devraient implémenter [`<`](@ref) au lieu de cette fonction, et s'appuyer sur la définition de repli `>(x, y) = y < x`.

# Exemples

```jldoctest
julia> 'a' > 'b'
false

julia> 7 > 3 > 1
true

julia> "abc" > "abd"
false

julia> 5 > 3
true
```
