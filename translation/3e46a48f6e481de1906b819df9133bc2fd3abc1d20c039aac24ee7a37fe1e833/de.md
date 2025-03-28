```
findall(A)
```

Gibt einen Vektor `I` der `true` Indizes oder Schlüssel von `A` zurück. Wenn es keine solchen Elemente von `A` gibt, wird ein leeres Array zurückgegeben. Um nach anderen Arten von Werten zu suchen, übergeben Sie ein Prädikat als erstes Argument.

Indizes oder Schlüssel sind vom gleichen Typ wie die von [`keys(A)`](@ref) und [`pairs(A)`](@ref) zurückgegebenen.

Siehe auch: [`findfirst`](@ref), [`searchsorted`](@ref).

# Beispiele

```jldoctest
julia> A = [true, false, false, true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> findall(A)
2-element Vector{Int64}:
 1
 4

julia> A = [true false; false true]
2×2 Matrix{Bool}:
 1  0
 0  1

julia> findall(A)
2-element Vector{CartesianIndex{2}}:
 CartesianIndex(1, 1)
 CartesianIndex(2, 2)

julia> findall(falses(3))
Int64[]
```
