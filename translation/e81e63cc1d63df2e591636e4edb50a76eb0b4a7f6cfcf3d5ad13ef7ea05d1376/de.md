```
dropzeros(x::AbstractCompressedVector)
```

Erzeugt eine Kopie von `x` und entfernt numerische Nullen aus dieser Kopie.

Für eine In-Place-Version und algorithmische Informationen siehe [`dropzeros!`](@ref).

# Beispiele

```jldoctest
julia> A = sparsevec([1, 2, 3], [1.0, 0.0, 1.0])
3-element SparseVector{Float64, Int64} mit 3 gespeicherten Einträgen:
  [1]  =  1.0
  [2]  =  0.0
  [3]  =  1.0

julia> dropzeros(A)
3-element SparseVector{Float64, Int64} mit 2 gespeicherten Einträgen:
  [1]  =  1.0
  [3]  =  1.0
```
