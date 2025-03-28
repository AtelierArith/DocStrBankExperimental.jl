```
findprev(A, i)
```

Finde den vorherigen Index vor oder einschließlich `i` eines `true`-Elements von `A`, oder `nothing`, wenn nichts gefunden wurde.

Indizes sind vom gleichen Typ wie die von [`keys(A)`](@ref) und [`pairs(A)`](@ref) zurückgegebenen.

Siehe auch: [`findnext`](@ref), [`findfirst`](@ref), [`findall`](@ref).

# Beispiele

```jldoctest
julia> A = [false, false, true, true]
4-element Vector{Bool}:
 0
 0
 1
 1

julia> findprev(A, 3)
3

julia> findprev(A, 1) # gibt nichts zurück, wird aber nicht im REPL angezeigt

julia> A = [false false; true true]
2×2 Matrix{Bool}:
 0  0
 1  1

julia> findprev(A, CartesianIndex(2, 1))
CartesianIndex(2, 1)
```
