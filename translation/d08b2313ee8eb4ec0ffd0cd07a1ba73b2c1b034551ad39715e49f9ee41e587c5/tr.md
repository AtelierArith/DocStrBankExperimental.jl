```
stride(A, k::Integer)
```

`k` boyutundaki bitişik elemanlar arasındaki bellek mesafesini (eleman sayısı cinsinden) döndürür.

Ayrıca bkz: [`strides`](@ref).

# Örnekler

```jldoctest
julia> A = fill(1, (3,4,5));

julia> stride(A,2)
3

julia> stride(A,3)
12
```
