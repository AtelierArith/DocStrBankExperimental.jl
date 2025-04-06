```
findnext(predicate::Function, A, i)
```

Finde den nächsten Index nach oder einschließlich `i` eines Elements von `A`, für das `predicate` `true` zurückgibt, oder `nothing`, wenn nichts gefunden wurde. Dies funktioniert für Arrays, Strings und die meisten anderen Sammlungen, die [`getindex`](@ref), [`keys(A)`](@ref) und [`nextind`](@ref) unterstützen.

Indizes sind vom gleichen Typ wie die, die von [`keys(A)`](@ref) und [`pairs(A)`](@ref) zurückgegeben werden.

# Beispiele

```jldoctest
julia> A = [1, 4, 2, 2];

julia> findnext(isodd, A, 1)
1

julia> findnext(isodd, A, 2) # gibt nichts zurück, wird aber nicht im REPL angezeigt

julia> A = [1 4; 2 2];

julia> findnext(isodd, A, CartesianIndex(1, 1))
CartesianIndex(1, 1)

julia> findnext(isspace, "a b c", 3)
4
```
