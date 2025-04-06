```
isdiag(A) -> Bool
```

Überprüfen, ob eine Matrix diagonal ist, im Sinne von `iszero(A[i,j])`, was wahr ist, es sei denn, `i == j`. Beachten Sie, dass es nicht notwendig ist, dass `A` quadratisch ist; wenn Sie das auch überprüfen möchten, müssen Sie sicherstellen, dass `size(A, 1) == size(A, 2)`.

# Beispiele

```jldoctest
julia> a = [1 2; 2 -1]
2×2 Matrix{Int64}:
 1   2
 2  -1

julia> isdiag(a)
false

julia> b = [im 0; 0 -im]
2×2 Matrix{Complex{Int64}}:
 0+1im  0+0im
 0+0im  0-1im

julia> isdiag(b)
true

julia> c = [1 0 0; 0 2 0]
2×3 Matrix{Int64}:
 1  0  0
 0  2  0

julia> isdiag(c)
true

julia> d = [1 0 0; 0 2 3]
2×3 Matrix{Int64}:
 1  0  0
 0  2  3

julia> isdiag(d)
false
```
