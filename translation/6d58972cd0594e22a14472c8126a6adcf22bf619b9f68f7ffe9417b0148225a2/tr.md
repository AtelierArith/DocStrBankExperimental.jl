```
sort(v; alg::Algorithm=defalg(v), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

[`sort!`](@ref) fonksiyonunun bir varyantı olup, `v`'yi değiştirmeden sıralı bir kopyasını döndürür.

# Örnekler

```jldoctest
julia> v = [3, 1, 2];

julia> sort(v)
3-element Vector{Int64}:
 1
 2
 3

julia> v
3-element Vector{Int64}:
 3
 1
 2
```
