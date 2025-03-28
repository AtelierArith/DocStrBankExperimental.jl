```
eigvals!(A; permute::Bool=true, scale::Bool=true, sortby) -> values
```

Igual que [`eigvals`](@ref), pero ahorra espacio al sobrescribir la entrada `A`, en lugar de crear una copia. Las palabras clave `permute`, `scale` y `sortby` son las mismas que para [`eigen`](@ref).

!!! nota
    La matriz de entrada `A` no contendrá sus valores propios después de que se llame a `eigvals!` sobre ella - `A` se utiliza como un espacio de trabajo.


# Ejemplos

```jldoctest
julia> A = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> eigvals!(A)
2-element Vector{Float64}:
 -0.3722813232690143
  5.372281323269014

julia> A
2×2 Matrix{Float64}:
 -0.372281  -1.0
  0.0        5.37228
```
