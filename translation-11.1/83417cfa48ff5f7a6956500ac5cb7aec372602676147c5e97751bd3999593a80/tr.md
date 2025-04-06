```
LinearAlgebra.checksquare(A)
```

Bir matrisin kare olup olmadığını kontrol edin, ardından ortak boyutunu döndürün. Birden fazla argüman için, bir vektör döndürün.

# Örnekler

```jldoctest
julia> A = fill(1, (4,4)); B = fill(1, (5,5));

julia> LinearAlgebra.checksquare(A, B)
2-element Vector{Int64}:
 4
 5
```
