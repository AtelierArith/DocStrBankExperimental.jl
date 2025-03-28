```
accumulate!(op, B, A; [dims], [init])
```

Kumulative Operation `op` auf `A` entlang der Dimension `dims`, wobei das Ergebnis in `B` gespeichert wird. Die Angabe von `dims` ist für Vektoren optional. Wenn das Schlüsselwort-Argument `init` angegeben wird, wird dessen Wert zur Instanziierung der Akkumulation verwendet.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein veränderter Parameter Speicher mit einem anderen Parameter teilt.


Siehe auch [`accumulate`](@ref), [`cumsum!`](@ref), [`cumprod!`](@ref).

# Beispiele

```jldoctest
julia> x = [1, 0, 2, 0, 3];

julia> y = rand(5);

julia> accumulate!(+, y, x);

julia> y
5-element Vector{Float64}:
 1.0
 1.0
 3.0
 3.0
 6.0

julia> A = [1 2 3; 4 5 6];

julia> B = similar(A);

julia> accumulate!(-, B, A, dims=1)
2×3 Matrix{Int64}:
  1   2   3
 -3  -3  -3

julia> accumulate!(*, B, A, dims=2, init=10)
2×3 Matrix{Int64}:
 10   20    60
 40  200  1200
```
