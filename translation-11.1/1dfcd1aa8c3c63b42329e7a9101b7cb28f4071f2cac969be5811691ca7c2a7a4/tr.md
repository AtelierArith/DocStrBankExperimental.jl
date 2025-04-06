```
popfirst!(koleksiyon) -> öğe
```

Koleksiyondan ilk `öğe`yi çıkarır.

Bu işlev birçok diğer programlama dilinde `shift` olarak adlandırılır.

Ayrıca bakınız: [`pop!`](@ref), [`popat!`](@ref), [`delete!`](@ref).

# Örnekler

```jldoctest
julia> A = [1, 2, 3, 4, 5, 6]
6-elemanlı Vektör{Int64}:
 1
 2
 3
 4
 5
 6

julia> popfirst!(A)
1

julia> A
5-elemanlı Vektör{Int64}:
 2
 3
 4
 5
 6
```
