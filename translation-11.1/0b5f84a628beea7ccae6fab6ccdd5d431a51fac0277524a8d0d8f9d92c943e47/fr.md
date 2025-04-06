```
axpy!(α, x::AbstractArray, y::AbstractArray)
```

Écrase `y` avec `x * α + y` et retourne `y`. Si `x` et `y` ont les mêmes axes, c'est équivalent à `y .+= x .* a`.

# Exemples

```jldoctest
julia> x = [1; 2; 3];

julia> y = [4; 5; 6];

julia> axpy!(2, x, y)
3-element Vector{Int64}:
  6
  9
 12
```
