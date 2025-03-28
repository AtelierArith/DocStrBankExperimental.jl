```
keepat!(a::Vector, m::AbstractVector{Bool})
keepat!(a::BitVector, m::AbstractVector{Bool})
```

La version en place de l'indexation logique `a = a[m]`. C'est-à-dire que `keepat!(a, m)` sur des vecteurs de même longueur `a` et `m` supprimera tous les éléments de `a` pour lesquels `m` à l'index correspondant est `false`.

# Exemples

```jldoctest
julia> a = [:a, :b, :c];

julia> keepat!(a, [true, false, true])
2-element Vector{Symbol}:
 :a
 :c

julia> a
2-element Vector{Symbol}:
 :a
 :c
```
