```
schur(A) -> F::Schur
```

Calcula la factorización de Schur de la matriz `A`. El factor de Schur (cuasi) triangular se puede obtener del objeto `Schur` `F` con `F.Schur` o `F.T` y los vectores de Schur ortogonales/unitarios se pueden obtener con `F.vectors` o `F.Z` de tal manera que `A = F.vectors * F.Schur * F.vectors'`. Los valores propios de `A` se pueden obtener con `F.values`.

Para `A` real, la factorización de Schur es "cuasitridimensional", lo que significa que es superior-triangular excepto con bloques diagonales de 2×2 para cualquier par conjugado de valores propios complejos; esto permite que la factorización sea puramente real incluso cuando hay valores propios complejos. Para obtener la factorización de Schur (compleja) puramente superior-triangular a partir de una factorización cuasitridimensional real, puedes usar `Schur{Complex}(schur(A))`.

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
valores propios:
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
