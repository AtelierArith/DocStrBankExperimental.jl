```
Bidiagonal(dv::V, ev::V, uplo::Symbol) where V <: AbstractVector
```

Konstruiert eine obere (`uplo=:U`) oder untere (`uplo=:L`) bidiagonale Matrix unter Verwendung der gegebenen Diagonal-(`dv`) und Off-Diagonal-(`ev`) Vektoren. Das Ergebnis ist vom Typ `Bidiagonal` und bietet effiziente spezialisierte lineare Solver, kann jedoch in eine reguläre Matrix mit [`convert(Array, _)`](@ref) (oder `Array(_)` für kurz) umgewandelt werden. Die Länge von `ev` muss um eins kleiner sein als die Länge von `dv`.

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

julia> Bu = Bidiagonal(dv, ev, :U) # ev ist auf der ersten Superdiagonale
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  7  ⋅  ⋅
 ⋅  2  8  ⋅
 ⋅  ⋅  3  9
 ⋅  ⋅  ⋅  4

julia> Bl = Bidiagonal(dv, ev, :L) # ev ist auf der ersten Subdiagonale
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  ⋅  ⋅  ⋅
 7  2  ⋅  ⋅
 ⋅  8  3  ⋅
 ⋅  ⋅  9  4
```
