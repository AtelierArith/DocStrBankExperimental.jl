```
LDLt <: Factorización
```

Tipo de factorización de matriz de la factorización `LDLt` de una matriz real [`SymTridiagonal`](@ref) `S` tal que `S = L*Diagonal(d)*L'`, donde `L` es una matriz [`UnitLowerTriangular`](@ref) y `d` es un vector. El uso principal de una factorización `LDLt` `F = ldlt(S)` es resolver el sistema de ecuaciones lineales `Sx = b` con `F\b`. Este es el tipo de retorno de [`ldlt`](@ref), la función de factorización de matriz correspondiente.

Los componentes individuales de la factorización `F::LDLt` se pueden acceder a través de `getproperty`:

| Componente | Descripción                                         |
|:----------:|:--------------------------------------------------- |
|   `F.L`    | `L` (parte triangular inferior unitaria) de `LDLt`  |
|   `F.D`    | `D` (parte diagonal) de `LDLt`                      |
|   `F.Lt`   | `Lt` (parte triangular superior unitaria) de `LDLt` |
|   `F.d`    | valores diagonales de `D` como un `Vector`          |

# Ejemplos

```jldoctest
julia> S = SymTridiagonal([3., 4., 5.], [1., 2.])
3×3 SymTridiagonal{Float64, Vector{Float64}}:
 3.0  1.0   ⋅
 1.0  4.0  2.0
  ⋅   2.0  5.0

julia> F = ldlt(S)
LDLt{Float64, SymTridiagonal{Float64, Vector{Float64}}}
Factor L:
3×3 UnitLowerTriangular{Float64, SymTridiagonal{Float64, Vector{Float64}}}:
 1.0        ⋅         ⋅
 0.333333  1.0        ⋅
 0.0       0.545455  1.0
Factor D:
3×3 Diagonal{Float64, Vector{Float64}}:
 3.0   ⋅        ⋅
  ⋅   3.66667   ⋅
  ⋅    ⋅       3.90909
```
