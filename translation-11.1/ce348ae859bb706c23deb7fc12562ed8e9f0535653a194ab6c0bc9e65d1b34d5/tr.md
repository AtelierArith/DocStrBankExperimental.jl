```
istriu(A::AbstractMatrix, k::Integer = 0) -> Bool
```

`A`'n `k`'nci süperdiagonalından başlayarak üst üçgen olup olmadığını test edin.

# Örnekler

```jldoctest
julia> a = [1 2; 2 -1]
2×2 Matrix{Int64}:
 1   2
 2  -1

julia> istriu(a)
false

julia> istriu(a, -1)
true

julia> c = [1 1 1; 1 1 1; 0 1 1]
3×3 Matrix{Int64}:
 1  1  1
 1  1  1
 0  1  1

julia> istriu(c)
false

julia> istriu(c, -1)
true
```
