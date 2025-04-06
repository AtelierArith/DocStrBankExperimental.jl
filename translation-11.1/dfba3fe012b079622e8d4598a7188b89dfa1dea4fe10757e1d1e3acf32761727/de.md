```
findfirst(A)
```

Gibt den Index oder Schlüssel des ersten `true` Wertes in `A` zurück. Gibt `nothing` zurück, wenn kein solcher Wert gefunden wird. Um nach anderen Arten von Werten zu suchen, übergeben Sie ein Prädikat als erstes Argument.

Indizes oder Schlüssel sind vom gleichen Typ wie die von [`keys(A)`](@ref) und [`pairs(A)`](@ref) zurückgegebenen.

Siehe auch: [`findall`](@ref), [`findnext`](@ref), [`findlast`](@ref), [`searchsortedfirst`](@ref).

# Beispiele

```jldoctest
julia> A = [false, false, true, false]
4-element Vector{Bool}:
 0
 0
 1
 0

julia> findfirst(A)
3

julia> findfirst(falses(3)) # gibt nichts zurück, wird aber nicht im REPL ausgegeben

julia> A = [false false; true false]
2×2 Matrix{Bool}:
 0  0
 1  0

julia> findfirst(A)
CartesianIndex(2, 1)
```
