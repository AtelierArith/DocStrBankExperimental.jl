```
cumsum(itr)
```

Bir iteratörün kümülatif toplamı.

Ayrıca `+` dışında fonksiyonlar uygulamak için [`accumulate`](@ref) bakın.

!!! compat "Julia 1.5"
    Bir dizi olmayan bir iteratörde `cumsum`, en az Julia 1.5 gerektirir.


# Örnekler

```jldoctest
julia> cumsum(1:3)
3-element Vector{Int64}:
 1
 3
 6

julia> cumsum((true, false, true, false, true))
(1, 1, 2, 2, 3)

julia> cumsum(fill(1, 2) for i in 1:3)
3-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 2]
 [3, 3]
```
