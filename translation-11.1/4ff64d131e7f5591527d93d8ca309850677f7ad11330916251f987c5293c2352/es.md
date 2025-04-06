```
ldlt(S::SymTridiagonal) -> LDLt
```

Calcula una factorización `LDLt` (es decir, $LDL^T$) de la matriz tridiagonal simétrica real `S` tal que `S = L*Diagonal(d)*L'` donde `L` es una matriz triangular inferior unitaria y `d` es un vector. El uso principal de una factorización `LDLt` `F = ldlt(S)` es resolver el sistema de ecuaciones lineales `Sx = b` con `F\b`.

Véase también [`bunchkaufman`](@ref) para una factorización similar, pero con pivoteo, de matrices simétricas o hermitianas arbitrarias.

# Ejemplos

```jldoctest
julia> S = SymTridiagonal([3., 4., 5.], [1., 2.])
3×3 SymTridiagonal{Float64, Vector{Float64}}:
 3.0  1.0   ⋅
 1.0  4.0  2.0
  ⋅   2.0  5.0

julia> ldltS = ldlt(S);

julia> b = [6., 7., 8.];

julia> ldltS \ b
3-element Vector{Float64}:
 1.7906976744186047
 0.627906976744186
 1.3488372093023255

julia> S \ b
3-element Vector{Float64}:
 1.7906976744186047
 0.627906976744186
 1.3488372093023255
```
