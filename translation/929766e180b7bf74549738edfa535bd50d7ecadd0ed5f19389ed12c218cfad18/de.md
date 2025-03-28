```
copyto!(dest::AbstractArray, src) -> dest
```

Kopiere alle Elemente aus der Sammlung `src` in das Array `dest`, dessen Länge größer oder gleich der Länge `n` von `src` sein muss. Die ersten `n` Elemente von `dest` werden überschrieben, die anderen Elemente bleiben unverändert.

Siehe auch [`copy!`](@ref Base.copy!), [`copy`](@ref).

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein mutiertes Argument Speicher mit einem anderen Argument teilt.


# Beispiele

```jldoctest
julia> x = [1., 0., 3., 0., 5.];

julia> y = zeros(7);

julia> copyto!(y, x);

julia> y
7-element Vector{Float64}:
 1.0
 0.0
 3.0
 0.0
 5.0
 0.0
 0.0
```
