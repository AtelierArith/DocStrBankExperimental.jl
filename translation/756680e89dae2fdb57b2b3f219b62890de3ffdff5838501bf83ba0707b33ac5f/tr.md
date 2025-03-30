```
ndims(A::AbstractArray) -> Integer
```

`A`'nın boyut sayısını döndürür.

Ayrıca bakınız: [`size`](@ref), [`axes`](@ref).

# Örnekler

```jldoctest
julia> A = fill(1, (3,4,5));

julia> ndims(A)
3
```
