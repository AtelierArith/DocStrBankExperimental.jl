```
istril(A::AbstractMatrix, k::Integer = 0) -> Bool
```

Überprüfen, ob `A` untere Dreiecksmatrix ist, beginnend von der `k`-ten Superdiagonale.

# Beispiele

```jldoctest
julia> a = [1 2; 2 -1]
2×2 Matrix{Int64}:
 1   2
 2  -1

julia> istril(a)
false

julia> istril(a, 1)
true

julia> c = [1 1 0; 1 1 1; 1 1 1]
3×3 Matrix{Int64}:
 1  1  0
 1  1  1
 1  1  1

julia> istril(c)
false

julia> istril(c, 1)
true
```
