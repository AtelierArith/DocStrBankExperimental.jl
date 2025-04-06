```
BitArray(itr)
```

Verilen iterable nesnesi tarafından oluşturulan bir [`BitArray`](@ref) oluşturur. Şekil `itr` nesnesinden çıkarılır.

# Örnekler

```jldoctest
julia> BitArray([1 0; 0 1])
2×2 BitMatrix:
 1  0
 0  1

julia> BitArray(x+y == 3 for x = 1:2, y = 1:3)
2×3 BitMatrix:
 0  1  0
 1  0  0

julia> BitArray(x+y == 3 for x = 1:2 for y = 1:3)
6-element BitVector:
 0
 1
 0
 1
 0
 0
```
