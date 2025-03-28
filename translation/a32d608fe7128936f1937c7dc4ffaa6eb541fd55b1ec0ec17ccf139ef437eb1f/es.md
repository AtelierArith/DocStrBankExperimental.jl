```
Schur <: Factorización
```

Tipo de factorización de matriz de la factorización de Schur de una matriz `A`. Este es el tipo de retorno de [`schur(_)`](@ref), la función de factorización de matriz correspondiente.

Si `F::Schur` es el objeto de factorización, el factor de Schur (cuasi) triangular se puede obtener a través de `F.Schur` o `F.T` y los vectores de Schur ortogonales/unitarios a través de `F.vectors` o `F.Z` de tal manera que `A = F.vectors * F.Schur * F.vectors'`. Los eigenvalores de `A` se pueden obtener con `F.values`.

Iterar la descomposición produce los componentes `F.T`, `F.Z` y `F.values`.

# Ejemplos

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> F = schur(A)
Schur{Float64, Matrix{Float64}, Vector{Float64}}
T factor:
2×2 Matrix{Float64}:
 3.0   9.0
 0.0  -2.0
Z factor:
2×2 Matrix{Float64}:
  0.961524  0.274721
 -0.274721  0.961524
eigenvalores:
2-element Vector{Float64}:
  3.0
 -2.0

julia> F.vectors * F.Schur * F.vectors'
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> t, z, vals = F; # desestructuración a través de la iteración

julia> t == F.T && z == F.Z && vals == F.values
true
```
