```
Tridiagonal(dl::V, d::V, du::V) where V <: AbstractVector
```

Konstruiere eine tridiagonale Matrix aus der ersten Subdiagonale, der Diagonale und der ersten Superdiagonale. Das Ergebnis ist vom Typ `Tridiagonal` und bietet effiziente spezialisierte lineare Solver, kann jedoch in eine reguläre Matrix mit [`convert(Array, _)`](@ref) (oder `Array(_)` für kurz) umgewandelt werden. Die Längen von `dl` und `du` müssen um eins kleiner sein als die Länge von `d`.

!!! Hinweis     Die Subdiagonale `dl` und die Superdiagonale `du` dürfen sich nicht gegenseitig aliasieren. Wenn ein Alias erkannt wird, verwendet der Konstruktor eine Kopie von `du` als Argument.

# Beispiele

```jldoctest
julia> dl = [1, 2, 3];

julia> du = [4, 5, 6];

julia> d = [7, 8, 9, 0];

julia> Tridiagonal(dl, d, du)
4×4 Tridiagonal{Int64, Vector{Int64}}:
 7  4  ⋅  ⋅
 1  8  5  ⋅
 ⋅  2  9  6
 ⋅  ⋅  3  0
```
