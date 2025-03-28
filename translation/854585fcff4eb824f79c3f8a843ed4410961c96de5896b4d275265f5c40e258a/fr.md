```
(I::UniformScaling)(n::Integer)
```

Construit une matrice `Diagonal` à partir d'un `UniformScaling`.

!!! compat "Julia 1.2"
    Cette méthode est disponible depuis Julia 1.2.


# Exemples

```jldoctest
julia> I(3)
3×3 Diagonal{Bool, Vector{Bool}}:
 1  ⋅  ⋅
 ⋅  1  ⋅
 ⋅  ⋅  1

julia> (0.7*I)(3)
3×3 Diagonal{Float64, Vector{Float64}}:
 0.7   ⋅    ⋅
  ⋅   0.7   ⋅
  ⋅    ⋅   0.7
```
