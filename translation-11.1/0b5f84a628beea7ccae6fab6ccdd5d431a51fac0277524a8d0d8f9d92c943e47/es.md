```
axpy!(α, x::AbstractArray, y::AbstractArray)
```

Sobrescribe `y` con `x * α + y` y devuelve `y`. Si `x` y `y` tienen los mismos ejes, es equivalente a `y .+= x .* a`.

# Ejemplos

```jldoctest
julia> x = [1; 2; 3];

julia> y = [4; 5; 6];

julia> axpy!(2, x, y)
3-element Vector{Int64}:
  6
  9
 12
```
