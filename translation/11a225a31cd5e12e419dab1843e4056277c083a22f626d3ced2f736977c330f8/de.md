```
LDLt <: Faktorisierung
```

Matrixfaktorisierungstyp der `LDLt`-Faktorisierung einer reellen [`SymTridiagonal`](@ref) Matrix `S`, sodass `S = L*Diagonal(d)*L'`, wobei `L` eine [`UnitLowerTriangular`](@ref) Matrix und `d` ein Vektor ist. Der Hauptzweck einer `LDLt`-Faktorisierung `F = ldlt(S)` besteht darin, das lineare Gleichungssystem `Sx = b` mit `F\b` zu lösen. Dies ist der Rückgabetyp von [`ldlt`](@ref), der entsprechenden Matrixfaktorisierungsfunktion.

Die einzelnen Komponenten der Faktorisierung `F::LDLt` können über `getproperty` zugegriffen werden:

| Komponente | Beschreibung                                            |
|:----------:|:------------------------------------------------------- |
|   `F.L`    | `L` (einheitlich untere Dreiecksmatrix) Teil von `LDLt` |
|   `F.D`    | `D` (diagonal) Teil von `LDLt`                          |
|   `F.Lt`   | `Lt` (einheitlich obere Dreiecksmatrix) Teil von `LDLt` |
|   `F.d`    | diagonale Werte von `D` als `Vector`                    |

# Beispiele

```jldoctest
julia> S = SymTridiagonal([3., 4., 5.], [1., 2.])
3×3 SymTridiagonal{Float64, Vector{Float64}}:
 3.0  1.0   ⋅
 1.0  4.0  2.0
  ⋅   2.0  5.0

julia> F = ldlt(S)
LDLt{Float64, SymTridiagonal{Float64, Vector{Float64}}}
L-Faktor:
3×3 UnitLowerTriangular{Float64, SymTridiagonal{Float64, Vector{Float64}}}:
 1.0        ⋅         ⋅
 0.333333  1.0        ⋅
 0.0       0.545455  1.0
D-Faktor:
3×3 Diagonal{Float64, Vector{Float64}}:
 3.0   ⋅        ⋅
  ⋅   3.66667   ⋅
  ⋅    ⋅       3.90909
```
