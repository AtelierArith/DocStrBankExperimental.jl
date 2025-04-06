```
(I::UniformScaling)(n::Integer)
```

Konstruiere eine `Diagonal`-Matrix aus einer `UniformScaling`.

!!! compat "Julia 1.2"
    Diese Methode ist seit Julia 1.2 verfügbar.


# Beispiele

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
