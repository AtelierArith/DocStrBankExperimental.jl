```
stride1(A) -> Int
```

Başka bir deyişle, eleman boyutu cinsinden boyut 1'deki ardışık dizi elemanları arasındaki mesafeyi döndürür.

# Örnekler

```jldoctest
julia> A = [1,2,3,4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> LinearAlgebra.stride1(A)
1

julia> B = view(A, 2:2:4)
2-element view(::Vector{Int64}, 2:2:4) with eltype Int64:
 2
 4

julia> LinearAlgebra.stride1(B)
2
```
