```
reim(A::AbstractArray)
```

Her bir girişin gerçek ve hayali kısmını içeren iki diziden oluşan bir demet döndürür `A`.

`(real.(A), imag.(A))` ile eşdeğerdir, ancak `eltype(A) <: Real` olduğunda `A` gerçek kısmı temsil etmek için kopyalanmadan döndürülür ve `A` sıfır boyutlu olduğunda, bir skalar yerine 0-boyutlu bir dizi döndürülür.

# Örnekler

```jldoctest
julia> reim([1, 2im, 3 + 4im])
([1, 0, 3], [0, 2, 4])

julia> reim(fill(2 - im))
(fill(2), fill(-1))
```
