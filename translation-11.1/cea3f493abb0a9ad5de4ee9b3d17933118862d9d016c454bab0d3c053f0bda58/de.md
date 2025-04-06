```
findprev(predicate::Function, A, i)
```

Finde den vorherigen Index vor oder einschließlich `i` eines Elements von `A`, für das `predicate` `true` zurückgibt, oder `nothing`, wenn nichts gefunden wurde. Dies funktioniert für Arrays, Strings und die meisten anderen Sammlungen, die [`getindex`](@ref), [`keys(A)`](@ref) und [`nextind`](@ref) unterstützen.

Indizes sind vom gleichen Typ wie die, die von [`keys(A)`](@ref) und [`pairs(A)`](@ref) zurückgegeben werden.

# Beispiele

```jldoctest
julia> A = [4, 6, 1, 2]
4-element Vector{Int64}:
 4
 6
 1
 2

julia> findprev(isodd, A, 1) # gibt nichts zurück, wird aber nicht im REPL angezeigt

julia> findprev(isodd, A, 3)
3

julia> A = [4 6; 1 2]
2×2 Matrix{Int64}:
 4  6
 1  2

julia> findprev(isodd, A, CartesianIndex(1, 2))
CartesianIndex(2, 1)

julia> findprev(isspace, "a b c", 3)
2
```
