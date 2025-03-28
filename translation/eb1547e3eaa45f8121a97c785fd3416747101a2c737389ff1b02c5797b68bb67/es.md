```
GeneralizedEigen <: Factorization
```

Tipo de factorización de matriz de la descomposición generalizada de valores propios/espectrales de `A` y `B`. Este es el tipo de retorno de [`eigen`](@ref), la función de factorización de matriz correspondiente, cuando se llama con dos argumentos de matriz.

Si `F::GeneralizedEigen` es el objeto de factorización, los valores propios se pueden obtener a través de `F.values` y los vectores propios como las columnas de la matriz `F.vectors`. (El `k`-ésimo vector propio se puede obtener de la porción `F.vectors[:, k]`.)

Iterar sobre la descomposición produce los componentes `F.values` y `F.vectors`.

# Ejemplos

```jldoctest
julia> A = [1 0; 0 -1]
2×2 Matrix{Int64}:
 1   0
 0  -1

julia> B = [0 1; 1 0]
2×2 Matrix{Int64}:
 0  1
 1  0

julia> F = eigen(A, B)
GeneralizedEigen{ComplexF64, ComplexF64, Matrix{ComplexF64}, Vector{ComplexF64}}
values:
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im
vectors:
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> F.values
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> F.vectors
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> vals, vecs = F; # destructuring via iteration

julia> vals == F.values && vecs == F.vectors
true
```
