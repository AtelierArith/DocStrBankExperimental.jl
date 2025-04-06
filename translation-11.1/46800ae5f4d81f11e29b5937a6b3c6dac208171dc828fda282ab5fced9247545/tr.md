```
reinterpret(reshape, T, A::AbstractArray{S}) -> B
```

`A`'nın tür yorumlamasını değiştirirken "kanal boyutu" ekleyin veya çıkarın.

Eğer `sizeof(T) = n*sizeof(S)` ve `n>1` ise, `A`'nın ilk boyutu `n` boyutunda olmalı ve `B`, `A`'nın ilk boyutunu içermez. Tersine, eğer `sizeof(S) = n*sizeof(T)` ve `n>1` ise, `B` yeni bir ilk boyut alır ve bu boyut `n`'dir. Eğer `sizeof(T) == sizeof(S)` ise, boyut değişmez.

!!! compat "Julia 1.6"
    Bu yöntem en az Julia 1.6 gerektirir.


# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> reinterpret(reshape, Complex{Int}, A)    # sonuç bir vektördür
2-element reinterpret(reshape, Complex{Int64}, ::Matrix{Int64}) with eltype Complex{Int64}:
 1 + 3im
 2 + 4im

julia> a = [(1,2,3), (4,5,6)]
2-element Vector{Tuple{Int64, Int64, Int64}}:
 (1, 2, 3)
 (4, 5, 6)

julia> reinterpret(reshape, Int, a)             # sonuç bir matristir
3×2 reinterpret(reshape, Int64, ::Vector{Tuple{Int64, Int64, Int64}}) with eltype Int64:
 1  4
 2  5
 3  6
```
