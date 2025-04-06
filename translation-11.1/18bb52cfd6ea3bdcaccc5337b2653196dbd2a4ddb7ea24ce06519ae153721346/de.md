```
keys(a::AbstractArray)
```

Gibt ein effizientes Array zurück, das alle gültigen Indizes für `a` beschreibt, angeordnet in der Form von `a` selbst.

Die Schlüssel von eindimensionalen Arrays (Vektoren) sind Ganzzahlen, während alle anderen N-dimensionalen Arrays [`CartesianIndex`](@ref) verwenden, um ihre Positionen zu beschreiben. Oft werden die speziellen Array-Typen [`LinearIndices`](@ref) und [`CartesianIndices`](@ref) verwendet, um diese Arrays von Ganzzahlen und `CartesianIndex`-Objekten effizient darzustellen.

Beachten Sie, dass die `keys` eines Arrays möglicherweise nicht der effizienteste Indextyp sind; für maximale Leistung verwenden Sie stattdessen [`eachindex`](@ref).

# Beispiele

```jldoctest
julia> keys([4, 5, 6])
3-element LinearIndices{1, Tuple{Base.OneTo{Int64}}}:
 1
 2
 3

julia> keys([4 5; 6 7])
CartesianIndices((2, 2))
```
