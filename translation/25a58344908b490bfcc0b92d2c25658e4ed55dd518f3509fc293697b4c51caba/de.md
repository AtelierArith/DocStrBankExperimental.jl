```
permute(A::AbstractSparseMatrixCSC{Tv,Ti}, p::AbstractVector{<:Integer},
        q::AbstractVector{<:Integer}) where {Tv,Ti}
```

Bilateral permutieren von `A`, Rückgabe von `PAQ` (`A[p,q]`). Die Länge der Spaltenpermutation `q` muss mit der Anzahl der Spalten von `A` übereinstimmen (`length(q) == size(A, 2)`). Die Länge der Zeilenpermutation `p` muss mit der Anzahl der Zeilen von `A` übereinstimmen (`length(p) == size(A, 1)`).

Für erfahrene Benutzer und zusätzliche Informationen siehe [`permute!`](@ref).

# Beispiele

```jldoctest
julia> A = spdiagm(0 => [1, 2, 3, 4], 1 => [5, 6, 7])
4×4 SparseMatrixCSC{Int64, Int64} mit 7 gespeicherten Einträgen:
 1  5  ⋅  ⋅
 ⋅  2  6  ⋅
 ⋅  ⋅  3  7
 ⋅  ⋅  ⋅  4

julia> permute(A, [4, 3, 2, 1], [1, 2, 3, 4])
4×4 SparseMatrixCSC{Int64, Int64} mit 7 gespeicherten Einträgen:
 ⋅  ⋅  ⋅  4
 ⋅  ⋅  3  7
 ⋅  2  6  ⋅
 1  5  ⋅  ⋅

julia> permute(A, [1, 2, 3, 4], [4, 3, 2, 1])
4×4 SparseMatrixCSC{Int64, Int64} mit 7 gespeicherten Einträgen:
 ⋅  ⋅  5  1
 ⋅  6  2  ⋅
 7  3  ⋅  ⋅
 4  ⋅  ⋅  ⋅
```
