```
I
```

Un objeto del tipo [`UniformScaling`](@ref), que representa una matriz identidad de cualquier tamaño.

# Ejemplos

```jldoctest
julia> fill(1, (5,6)) * I == fill(1, (5,6))
true

julia> [1 2im 3; 1im 2 3] * I
2×3 Matrix{Complex{Int64}}:
 1+0im  0+2im  3+0im
 0+1im  2+0im  3+0im
```
