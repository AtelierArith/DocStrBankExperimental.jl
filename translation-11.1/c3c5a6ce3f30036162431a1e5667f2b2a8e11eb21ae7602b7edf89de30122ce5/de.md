```
nonzeros(A)
```

Gibt einen Vektor der strukturellen Nicht-Null-Werte im spärlichen Array `A` zurück. Dies umfasst Nullen, die explizit im spärlichen Array gespeichert sind. Der zurückgegebene Vektor verweist direkt auf den internen Nicht-Null-Speicher von `A`, und alle Änderungen am zurückgegebenen Vektor werden auch `A` verändern. Siehe [`rowvals`](@ref) und [`nzrange`](@ref).

# Beispiele

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} mit 3 gespeicherten Einträgen:
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> nonzeros(A)
3-element Vector{Int64}:
 2
 2
 2
```
