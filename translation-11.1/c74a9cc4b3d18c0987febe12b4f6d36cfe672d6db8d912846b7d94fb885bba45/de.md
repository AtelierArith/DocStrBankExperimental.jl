```
SymTridiagonal(dv::V, ev::V) where V <: AbstractVector
```

Konstruiere eine symmetrische tridiagonale Matrix aus der Diagonale (`dv`) und der ersten Unter-/Überdiagonale (`ev`). Das Ergebnis ist vom Typ `SymTridiagonal` und bietet effiziente spezialisierte Eigenlöser, kann jedoch in eine reguläre Matrix mit [`convert(Array, _)`](@ref) (oder `Array(_)` für kurz) umgewandelt werden.

Für `SymTridiagonal` Blockmatrizen werden die Elemente von `dv` symmetriert. Das Argument `ev` wird als Überdiagonale interpretiert. Blöcke von der Unterdiagonale sind (materialisierte) Transponierte der entsprechenden Überdiagonalblöcke.

# Beispiele

```jldoctest
julia> dv = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> ev = [7, 8, 9]
3-element Vector{Int64}:
 7
 8
 9

julia> SymTridiagonal(dv, ev)
4×4 SymTridiagonal{Int64, Vector{Int64}}:
 1  7  ⋅  ⋅
 7  2  8  ⋅
 ⋅  8  3  9
 ⋅  ⋅  9  4

julia> A = SymTridiagonal(fill([1 2; 3 4], 3), fill([1 2; 3 4], 2));

julia> A[1,1]
2×2 Symmetric{Int64, Matrix{Int64}}:
 1  2
 2  4

julia> A[1,2]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> A[2,1]
2×2 Matrix{Int64}:
 1  3
 2  4
```
