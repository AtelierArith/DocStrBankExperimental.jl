```
\(x, y)
```

Opérateur de division à gauche : multiplication de `y` par l'inverse de `x` à gauche. Donne des résultats en virgule flottante pour des arguments entiers.

# Exemples

```jldoctest
julia> 3 \ 6
2.0

julia> inv(3) * 6
2.0

julia> A = [4 3; 2 1]; x = [5, 6];

julia> A \ x
2-element Vector{Float64}:
  6.5
 -7.0

julia> inv(A) * x
2-element Vector{Float64}:
  6.5
 -7.0
```
