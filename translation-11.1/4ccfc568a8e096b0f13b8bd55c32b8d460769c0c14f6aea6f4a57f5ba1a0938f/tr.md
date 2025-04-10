```
cumprod(itr)
```

Bir iteratörün kümülatif çarpımı.

Ayrıca bkz. [`cumprod!`](@ref), [`accumulate`](@ref), [`cumsum`](@ref).

!!! uyumluluk "Julia 1.5"
    Bir dizi olmayan bir iteratörde `cumprod` en az Julia 1.5 gerektirir.


# Örnekler

```jldoctest
julia> cumprod(fill(1//2, 3))
3-element Vector{Rational{Int64}}:
 1//2
 1//4
 1//8

julia> cumprod((1, 2, 1, 3, 1))
(1, 2, 2, 6, 6)

julia> cumprod("julia")
5-element Vector{String}:
 "j"
 "ju"
 "jul"
 "juli"
 "julia"
```
