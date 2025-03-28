```
real(A::AbstractArray)
```

Gibt ein Array zurück, das den Realteil jedes Eintrags im Array `A` enthält.

Entspricht `real.(A)`, mit dem Unterschied, dass wenn `eltype(A) <: Real` `A` ohne Kopieren zurückgegeben wird und dass wenn `A` null Dimensionen hat, ein 0-dimensionales Array zurückgegeben wird (anstatt eines Skalars).

# Beispiele

```jldoctest
julia> real([1, 2im, 3 + 4im])
3-element Vector{Int64}:
 1
 0
 3

julia> real(fill(2 - im))
0-dimensional Array{Int64, 0}:
2
```
