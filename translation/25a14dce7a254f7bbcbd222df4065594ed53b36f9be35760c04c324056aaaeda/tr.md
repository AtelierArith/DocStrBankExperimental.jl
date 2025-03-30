```
insert!(a::Vector, index::Integer, item)
```

Bir `item`'i verilen `index`'te `a`'ya ekleyin. `index`, `item`'in sonuçta oluşan `a` içindeki indeksidir.

Ayrıca bakınız: [`push!`](@ref), [`replace`](@ref), [`popat!`](@ref), [`splice!`](@ref).

# Örnekler

```jldoctest
julia> insert!(Any[1:6;], 3, "here")
7-element Vector{Any}:
 1
 2
  "here"
 3
 4
 5
 6
```
