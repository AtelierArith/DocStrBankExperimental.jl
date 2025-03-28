```
Eigen <: Factorization
```

Tipo de factorización de matriz de la descomposición en valores propios/espectrales de una matriz cuadrada `A`. Este es el tipo de retorno de [`eigen`](@ref), la función de factorización de matriz correspondiente.

Si `F::Eigen` es el objeto de factorización, los valores propios se pueden obtener a través de `F.values` y los vectores propios como las columnas de la matriz `F.vectors`. (El `k`-ésimo vector propio se puede obtener del segmento `F.vectors[:, k]`.)

Iterar sobre la descomposición produce los componentes `F.values` y `F.vectors`.

# Ejemplos

```jldoctest
julia> F = eigen([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
Eigen{Float64, Float64, Matrix{Float64}, Vector{Float64}}
values:
3-element Vector{Float64}:
  1.0
  3.0
 18.0
vectors:
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> F.values
3-element Vector{Float64}:
  1.0
  3.0
 18.0

julia> F.vectors
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> vals, vecs = F; # destructuring via iteration

julia> vals == F.values && vecs == F.vectors
true
```
