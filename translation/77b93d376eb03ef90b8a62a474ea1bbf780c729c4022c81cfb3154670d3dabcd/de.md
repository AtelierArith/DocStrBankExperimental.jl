```
partialsortperm!(ix, v, k; by=identity, lt=isless, rev=false)
```

Wie [`partialsortperm`](@ref), aber akzeptiert einen vorab zugewiesenen Indexvektor `ix`, der die gleiche Größe wie `v` hat und verwendet wird, um (eine Permutation von) den Indizes von `v` zu speichern.

`ix` wird initialisiert, um die Indizes von `v` zu enthalten.

(Typischerweise werden die Indizes von `v` `1:length(v)` sein, obwohl, wenn `v` einen alternativen Array-Typ mit nicht-einsbasierten Indizes hat, wie z.B. ein `OffsetArray`, `ix` diese gleichen Indizes teilen muss)

Bei der Rückkehr ist garantiert, dass `ix` die Indizes `k` in ihren sortierten Positionen hat, sodass

```julia
partialsortperm!(ix, v, k);
v[ix[k]] == partialsort(v, k)
```

Der Rückgabewert ist das `k`-te Element von `ix`, wenn `k` eine Ganzzahl ist, oder eine Ansicht in `ix`, wenn `k` ein Bereich ist.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein mutierter Parameter Speicher mit einem anderen Parameter teilt.


# Beispiele

```jldoctest
julia> v = [3, 1, 2, 1];

julia> ix = Vector{Int}(undef, 4);

julia> partialsortperm!(ix, v, 1)
2

julia> ix = [1:4;];

julia> partialsortperm!(ix, v, 2:3)
2-element view(::Vector{Int64}, 2:3) with eltype Int64:
 4
 3
```

```
