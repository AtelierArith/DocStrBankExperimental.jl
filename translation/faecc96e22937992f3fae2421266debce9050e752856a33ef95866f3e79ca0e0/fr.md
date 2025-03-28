```
resize!(a::Vector, n::Integer) -> Vector
```

Redimensionne `a` pour contenir `n` éléments. Si `n` est inférieur à la longueur actuelle de la collection, les premiers `n` éléments seront conservés. Si `n` est supérieur, les nouveaux éléments ne sont pas garantis d'être initialisés.

# Exemples

```jldoctest
julia> resize!([6, 5, 4, 3, 2, 1], 3)
3-element Vector{Int64}:
 6
 5
 4

julia> a = resize!([6, 5, 4, 3, 2, 1], 8);

julia> length(a)
8

julia> a[1:6]
6-element Vector{Int64}:
 6
 5
 4
 3
 2
 1
```
