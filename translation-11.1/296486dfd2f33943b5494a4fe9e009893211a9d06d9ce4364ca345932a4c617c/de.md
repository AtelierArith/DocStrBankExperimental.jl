```
LinearIndices(A::AbstractArray)
```

Gibt ein `LinearIndices`-Array mit derselben Form und [`axes`](@ref) wie `A` zurück, das den linearen Index jedes Eintrags in `A` enthält. Das Indizieren dieses Arrays mit kartesischen Indizes ermöglicht die Zuordnung zu linearen Indizes.

Für Arrays mit konventioneller Indizierung (Indizes beginnen bei 1) oder für beliebige mehrdimensionale Arrays reichen die linearen Indizes von 1 bis `length(A)`. Für `AbstractVector`s sind die linearen Indizes jedoch `axes(A, 1)`, und beginnen daher nicht bei 1 für Vektoren mit unkonventioneller Indizierung.

Diese Funktion aufzurufen ist der "sichere" Weg, um Algorithmen zu schreiben, die lineare Indizierung nutzen.

# Beispiele

```jldoctest
julia> A = fill(1, (5,6,7));

julia> b = LinearIndices(A);

julia> extrema(b)
(1, 210)
```

```
LinearIndices(inds::CartesianIndices) -> R
LinearIndices(sz::Dims) -> R
LinearIndices((istart:istop, jstart:jstop, ...)) -> R
```

Gibt ein `LinearIndices`-Array mit der angegebenen Form oder [`axes`](@ref) zurück.

# Beispiele

Der Hauptzweck dieses Konstruktors ist die intuitive Umwandlung von kartesischer in lineare Indizierung:

```jldoctest
julia> linear = LinearIndices((1:3, 1:2))
3×2 LinearIndices{2, Tuple{UnitRange{Int64}, UnitRange{Int64}}}:
 1  4
 2  5
 3  6

julia> linear[1,2]
4
```
