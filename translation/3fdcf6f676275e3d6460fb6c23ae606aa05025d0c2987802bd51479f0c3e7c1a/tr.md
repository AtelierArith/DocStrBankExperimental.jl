```
rotl90(A, k)
```

Matris `A`'yı `k` kadar tam sayı ile saat yönünün tersine 90 derece sola döndürür. Eğer `k` dörtün katı (sıfır dahil) ise, bu bir `copy` ile eşdeğerdir.

# Örnekler

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rotl90(a,1)
2×2 Matrix{Int64}:
 2  4
 1  3

julia> rotl90(a,2)
2×2 Matrix{Int64}:
 4  3
 2  1

julia> rotl90(a,3)
2×2 Matrix{Int64}:
 3  1
 4  2

julia> rotl90(a,4)
2×2 Matrix{Int64}:
 1  2
 3  4
```
