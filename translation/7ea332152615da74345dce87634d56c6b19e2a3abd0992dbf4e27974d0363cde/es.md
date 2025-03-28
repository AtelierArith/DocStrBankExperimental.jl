```
eigvals!(A, B; sortby) -> values
```

Igual que [`eigvals`](@ref), pero ahorra espacio al sobrescribir la entrada `A` (y `B`), en lugar de crear copias.

!!! note
    Las matrices de entrada `A` y `B` no contendrán sus valores propios después de que se llame a `eigvals!`. Se utilizan como espacios de trabajo.


# Ejemplos

```jldoctest
julia> A = [1. 0.; 0. -1.]
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> B = [0. 1.; 1. 0.]
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> eigvals!(A, B)
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> A
2×2 Matrix{Float64}:
 -0.0  -1.0
  1.0  -0.0

julia> B
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
