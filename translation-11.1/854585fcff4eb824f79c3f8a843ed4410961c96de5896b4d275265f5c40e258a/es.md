```
(I::UniformScaling)(n::Integer)
```

Construye una matriz `Diagonal` a partir de un `UniformScaling`.

!!! compat "Julia 1.2"
    Este método está disponible a partir de Julia 1.2.


# Ejemplos

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
