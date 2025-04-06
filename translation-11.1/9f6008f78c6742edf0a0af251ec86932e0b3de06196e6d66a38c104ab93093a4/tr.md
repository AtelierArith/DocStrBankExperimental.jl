```
deleteat!(a::Vector, i::Integer)
```

Verilen `i`'deki öğeyi kaldırır ve değiştirilmiş `a`'yı döndürür. Sonraki öğeler, oluşan boşluğu doldurmak için kaydırılır.

Ayrıca bakınız: [`keepat!`](@ref), [`delete!`](@ref), [`popat!`](@ref), [`splice!`](@ref).

# Örnekler

```jldoctest
julia> deleteat!([6, 5, 4, 3, 2, 1], 2)
5-element Vector{Int64}:
 6
 4
 3
 2
 1
```
