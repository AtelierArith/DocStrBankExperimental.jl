```
real(A::AbstractArray)
```

Dizi `A`'deki her bir elemanın reel kısmını içeren bir dizi döndürür.

`real.(A)` ile eşdeğerdir, ancak `eltype(A) <: Real` olduğunda `A` kopyalanmadan döndürülür ve `A` sıfır boyutlu olduğunda bir skalar yerine 0-boyutlu bir dizi döndürülür.

# Örnekler

```jldoctest
julia> real([1, 2im, 3 + 4im])
3-element Vector{Int64}:
 1
 0
 3

julia> real(fill(2 - im))
0-boyutlu Array{Int64, 0}:
2
```
