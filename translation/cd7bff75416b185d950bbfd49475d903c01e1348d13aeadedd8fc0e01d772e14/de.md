```
map!(funktion, ziel, sammlung...)
```

Wie [`map`](@ref), aber speichert das Ergebnis in `ziel` anstelle einer neuen Sammlung. `ziel` muss mindestens so groß sein wie die kleinste Sammlung.

!!! warnung
    Das Verhalten kann unerwartet sein, wenn ein mutiertes Argument Speicher mit einem anderen Argument teilt.


Siehe auch: [`map`](@ref), [`foreach`](@ref), [`zip`](@ref), [`copyto!`](@ref).

# Beispiele

```jldoctest
julia> a = zeros(3);

julia> map!(x -> x * 2, a, [1, 2, 3]);

julia> a
3-element Vector{Float64}:
 2.0
 4.0
 6.0

julia> map!(+, zeros(Int, 5), 100:999, 1:3)
5-element Vector{Int64}:
 101
 103
 105
   0
   0
```
