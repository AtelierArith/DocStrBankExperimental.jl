```
axpby!(α, x::AbstractArray, β, y::AbstractArray)
```

Überschreibe `y` mit `x * α + y * β` und gebe `y` zurück. Wenn `x` und `y` die gleichen Achsen haben, ist es äquivalent zu `y .= x .* a .+ y .* β`.

# Beispiele

```jldoctest
julia> x = [1; 2; 3];

julia> y = [4; 5; 6];

julia> axpby!(2, x, 2, y)
3-element Vector{Int64}:
 10
 14
 18
```
