```
conj(A::AbstractArray)
```

Dizi `A`'deki her bir elemanın karmaşık eşleniğini içeren bir dizi döndürür.

`conj.(A)` ile eşdeğerdir, ancak `eltype(A) <: Real` olduğunda `A` kopyalanmadan döndürülür ve `A` sıfır boyutlu olduğunda bir skalar yerine 0-boyutlu bir dizi döndürülür.

# Örnekler

```jldoctest
julia> conj([1, 2im, 3 + 4im])
3-element Vector{Complex{Int64}}:
 1 + 0im
 0 - 2im
 3 - 4im

julia> conj(fill(2 - im))
0-boyutlu Array{Complex{Int64}, 0}:
2 + 1im
```
