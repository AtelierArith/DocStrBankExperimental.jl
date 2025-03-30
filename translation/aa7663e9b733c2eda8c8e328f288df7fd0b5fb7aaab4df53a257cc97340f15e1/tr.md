```
rotr90(A, k)
```

Matris `A`'yı saat yönünde `k` kez 90 derece döndürür. Eğer `k` dörtün katıysa (sıfır dahil), bu bir `copy` ile eşdeğerdir.

# Örnekler

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rotr90(a,1)
2×2 Matrix{Int64}:
 3  1
 4  2

julia> rotr90(a,2)
2×2 Matrix{Int64}:
 4  3
 2  1

julia> rotr90(a,3)
2×2 Matrix{Int64}:
 2  4
 1  3

julia> rotr90(a,4)
2×2 Matrix{Int64}:
 1  2
 3  4
```
