```
imag(A::AbstractArray)
```

Dizi `A`'deki her bir elemanın hayali kısmını içeren bir dizi döndürür.

`imag.(A)` ile eşdeğerdir, ancak `A` sıfır boyutlu olduğunda, bir skalar yerine 0-boyutlu bir dizi döndürülür.

# Örnekler

```jldoctest
julia> imag([1, 2im, 3 + 4im])
3-element Vector{Int64}:
 0
 2
 4

julia> imag(fill(2 - im))
0-boyutlu Array{Int64, 0}:
-1
```
