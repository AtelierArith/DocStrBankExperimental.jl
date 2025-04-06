```
circcopy!(dest, src)
```

Kopiere `src` nach `dest`, indem jede Dimension modulo ihrer Länge indiziert wird. `src` und `dest` müssen die gleiche Größe haben, können jedoch in ihren Indizes versetzt sein; jede Versetzung führt zu einer (zirkulären) Umwicklung. Wenn die Arrays überlappende Indizes haben, dann stimmt `dest` im Bereich der Überlappung mit `src` überein.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein veränderter Parameter Speicher mit einem anderen Parameter teilt.


Siehe auch: [`circshift`](@ref).

# Beispiele

```julia-repl
julia> src = reshape(Vector(1:16), (4,4))
4×4 Array{Int64,2}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> dest = OffsetArray{Int}(undef, (0:3,2:5))

julia> circcopy!(dest, src)
OffsetArrays.OffsetArray{Int64,2,Array{Int64,2}} mit Indizes 0:3×2:5:
 8  12  16  4
 5   9  13  1
 6  10  14  2
 7  11  15  3

julia> dest[1:3,2:4] == src[1:3,2:4]
true
```
