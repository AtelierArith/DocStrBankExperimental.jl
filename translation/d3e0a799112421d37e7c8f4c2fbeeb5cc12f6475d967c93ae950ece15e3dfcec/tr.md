```
diff(A::AbstractVector)
diff(A::AbstractArray; dims::Integer)
```

Bir vektör veya çok boyutlu bir dizi `A` üzerindeki sonlu fark operatörü. İkinci durumda, işlem yapılacak boyut `dims` anahtar kelime argümanı ile belirtilmelidir.

!!! uyumluluk "Julia 1.1"
    2'den daha yüksek boyutlu diziler için `diff`, en az Julia 1.1 gerektirir.


# Örnekler

```jldoctest
julia> a = [2 4; 6 16]
2×2 Matrix{Int64}:
 2   4
 6  16

julia> diff(a, dims=2)
2×1 Matrix{Int64}:
  2
 10

julia> diff(vec(a))
3-element Vector{Int64}:
  4
 -2
 12
```
