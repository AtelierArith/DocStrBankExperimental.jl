```
conj(A::AbstractArray)
```

Gibt ein Array zurück, das den komplexen Konjugierten jedes Eintrags im Array `A` enthält.

Entspricht `conj.(A)`, mit dem Unterschied, dass wenn `eltype(A) <: Real`, `A` ohne Kopie zurückgegeben wird, und dass wenn `A` null Dimensionen hat, ein 0-dimensionales Array zurückgegeben wird (anstatt eines Skalars).

# Beispiele

```jldoctest
julia> conj([1, 2im, 3 + 4im])
3-element Vector{Complex{Int64}}:
 1 + 0im
 0 - 2im
 3 - 4im

julia> conj(fill(2 - im))
0-dimensional Array{Complex{Int64}, 0}:
2 + 1im
```
