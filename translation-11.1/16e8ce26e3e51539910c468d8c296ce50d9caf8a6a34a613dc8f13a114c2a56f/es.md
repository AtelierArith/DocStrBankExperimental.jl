```
axpby!(α, x::AbstractArray, β, y::AbstractArray)
```

Sobrescribe `y` con `x * α + y * β` y devuelve `y`. Si `x` y `y` tienen los mismos ejes, es equivalente a `y .= x .* a .+ y .* β`.

# Ejemplos

```jldoctest
julia> x = [1; 2; 3];

julia> y = [4; 5; 6];

julia> axpby!(2, x, 2, y)
3-element Vector{Int64}:
 10
 14
 18
```
