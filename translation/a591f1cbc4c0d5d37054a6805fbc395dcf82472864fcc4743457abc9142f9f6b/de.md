```
rowvals(A::AbstractSparseMatrixCSC)
```

Gibt einen Vektor der Zeilenindizes von `A` zurück. Änderungen am zurückgegebenen Vektor wirken sich ebenfalls auf `A` aus. Der Zugriff darauf, wie die Zeilenindizes intern gespeichert sind, kann nützlich sein, um über strukturelle Nicht-Null-Werte zu iterieren. Siehe auch [`nonzeros`](@ref) und [`nzrange`](@ref).

# Beispiele

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} mit 3 gespeicherten Einträgen:
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> rowvals(A)
3-element Vector{Int64}:
 1
 2
 3
```
