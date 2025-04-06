```
diagind(M::AbstractMatrix, k::Integer = 0, indstyle::IndexStyle = IndexLinear())
diagind(M::AbstractMatrix, indstyle::IndexStyle = IndexLinear())
```

Ein `AbstractRange`, der die Indizes der `k`-ten Diagonale der Matrix `M` angibt. Optional kann ein Indexstil angegeben werden, der den Typ des zurückgegebenen Bereichs bestimmt. Wenn `indstyle isa IndexLinear` (Standard), gibt dies einen `AbstractRange{Integer}` zurück. Andererseits, wenn `indstyle isa IndexCartesian`, gibt dies einen `AbstractRange{CartesianIndex{2}}` zurück.

Wenn `k` nicht angegeben ist, wird angenommen, dass es `0` ist (entsprechend der Hauptdiagonale).

Siehe auch: [`diag`](@ref), [`diagm`](@ref), [`Diagonal`](@ref).

# Beispiele

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> diagind(A, -1)
2:4:6

julia> diagind(A, IndexCartesian())
StepRangeLen(CartesianIndex(1, 1), CartesianIndex(1, 1), 3)
```

!!! compat "Julia 1.11"
    Die Angabe eines `IndexStyle` erfordert mindestens Julia 1.11.

