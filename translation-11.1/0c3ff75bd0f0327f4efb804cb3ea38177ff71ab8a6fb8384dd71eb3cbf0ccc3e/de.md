```
findnext(A, i)
```

Finde den nächsten Index nach oder einschließlich `i` eines `true`-Elements von `A`, oder `nothing`, wenn nicht gefunden.

Indizes sind vom gleichen Typ wie die von [`keys(A)`](@ref) und [`pairs(A)`](@ref) zurückgegebenen.

# Beispiele

```jldoctest
julia> A = [false, false, true, false]
4-element Vector{Bool}:
 0
 0
 1
 0

julia> findnext(A, 1)
3

julia> findnext(A, 4) # gibt nothing zurück, wird aber nicht im REPL angezeigt

julia> A = [false false; true false]
2×2 Matrix{Bool}:
 0  0
 1  0

julia> findnext(A, CartesianIndex(1, 1))
CartesianIndex(2, 1)
```
