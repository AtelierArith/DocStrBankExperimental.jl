```
ldlt(S::SymTridiagonal) -> LDLt
```

Berechne eine `LDLt` (d.h. $LDL^T$) Faktorisierung der reellen symmetrischen tridiagonalen Matrix `S`, sodass `S = L*Diagonal(d)*L'`, wobei `L` eine einheitsuntere Dreiecksmatrix und `d` ein Vektor ist. Der Hauptzweck einer `LDLt`-Faktorisierung `F = ldlt(S)` besteht darin, das lineare Gleichungssystem `Sx = b` mit `F\b` zu lösen.

Siehe auch [`bunchkaufman`](@ref) für eine ähnliche, aber pivotierte Faktorisierung beliebiger symmetrischer oder hermitescher Matrizen.

# Beispiele

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
