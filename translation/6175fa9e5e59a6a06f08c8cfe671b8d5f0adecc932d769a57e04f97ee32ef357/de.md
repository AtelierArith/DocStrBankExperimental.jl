```
rot180(A, k)
```

Drehe die Matrix `A` um 180 Grad eine ganze Zahl `k` Mal. Wenn `k` gerade ist, entspricht dies einer `Kopie`.

# Beispiele

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rot180(a,1)
2×2 Matrix{Int64}:
 4  3
 2  1

julia> rot180(a,2)
2×2 Matrix{Int64}:
 1  2
 3  4
```
