```
conj!(A)
```

Transformiere ein Array in seinen komplexen Konjugierten vor Ort.

Siehe auch [`conj`](@ref).

# Beispiele

```jldoctest
julia> A = [1+im 2-im; 2+2im 3+im]
2×2 Matrix{Complex{Int64}}:
 1+1im  2-1im
 2+2im  3+1im

julia> conj!(A);

julia> A
2×2 Matrix{Complex{Int64}}:
 1-1im  2+1im
 2-2im  3-1im
```
