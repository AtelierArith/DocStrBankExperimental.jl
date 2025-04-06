```
sort(v; alg::Algorithm=defalg(v), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Variante von [`sort!`](@ref), die eine sortierte Kopie von `v` zurückgibt, wobei `v` selbst unverändert bleibt.

# Beispiele

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
