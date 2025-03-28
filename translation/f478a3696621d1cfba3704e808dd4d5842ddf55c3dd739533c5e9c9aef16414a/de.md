```
getindex(A, inds...)
```

Gibt eine Teilmenge des Arrays `A` zurück, die durch die Indizes `inds` ausgewählt wurde.

Jeder Index kann ein [unterstützter Indextyp](@ref man-supported-index-types) sein, wie z.B. ein [`Integer`](@ref), [`CartesianIndex`](@ref), [Bereich](@ref Base.AbstractRange) oder [Array](@ref man-multi-dim-arrays) von unterstützten Indizes. Ein [:](@ref Base.Colon) kann verwendet werden, um alle Elemente entlang einer bestimmten Dimension auszuwählen, und ein boolesches Array (z.B. ein `Array{Bool}` oder ein [`BitArray`](@ref)) kann verwendet werden, um Elemente zu filtern, bei denen der entsprechende Index `true` ist.

Wenn `inds` mehrere Elemente auswählt, gibt diese Funktion ein neu zugewiesenes Array zurück. Um mehrere Elemente zu indizieren, ohne eine Kopie zu erstellen, verwenden Sie stattdessen [`view`](@ref).

Siehe den Abschnitt im Handbuch über [Array-Indizierung](@ref man-array-indexing) für weitere Details.

# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> getindex(A, 1)
1

julia> getindex(A, [2, 1])
2-element Vector{Int64}:
 3
 1

julia> getindex(A, 2:4)
3-element Vector{Int64}:
 3
 2
 4

julia> getindex(A, 2, 1)
3

julia> getindex(A, CartesianIndex(2, 1))
3

julia> getindex(A, :, 2)
2-element Vector{Int64}:
 2
 4

julia> getindex(A, 2, :)
2-element Vector{Int64}:
 3
 4

julia> getindex(A, A .> 2)
2-element Vector{Int64}:
 3
 4
```
