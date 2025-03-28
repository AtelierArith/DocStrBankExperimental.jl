```
maximum(f, A::AbstractArray; dims)
```

Berechne den maximalen Wert, indem die Funktion `f` auf jedes Element eines Arrays über die angegebenen Dimensionen angewendet wird.

# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> maximum(abs2, A, dims=1)
1×2 Matrix{Int64}:
 9  16

julia> maximum(abs2, A, dims=2)
2×1 Matrix{Int64}:
  4
 16
```
