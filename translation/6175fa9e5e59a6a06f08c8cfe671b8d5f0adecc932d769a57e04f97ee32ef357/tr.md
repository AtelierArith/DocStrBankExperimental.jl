```
rot180(A, k)
```

Matris `A`'yı 180 derece döndür ve `k` kadar tam sayı ile döndür. Eğer `k` çift ise, bu bir `kopya` ile eşdeğerdir.

# Örnekler

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
