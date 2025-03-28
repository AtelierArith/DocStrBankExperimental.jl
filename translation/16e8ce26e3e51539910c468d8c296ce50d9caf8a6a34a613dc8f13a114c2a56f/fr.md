```
axpby!(α, x::AbstractArray, β, y::AbstractArray)
```

Écrase `y` avec `x * α + y * β` et retourne `y`. Si `x` et `y` ont les mêmes axes, c'est équivalent à `y .= x .* a .+ y .* β`.

# Exemples

```jldoctest
julia> x = [1; 2; 3];

julia> y = [4; 5; 6];

julia> axpby!(2, x, 2, y)
3-element Vector{Int64}:
 10
 14
 18
```
