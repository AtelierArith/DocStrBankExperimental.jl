```
strides(A)
```

Her boyut için bellek adımlarının bir demetini döndürür.

Ayrıca bkz: [`stride`](@ref).

# Örnekler

```jldoctest
julia> A = fill(1, (3,4,5));

julia> strides(A)
(1, 3, 12)
```
