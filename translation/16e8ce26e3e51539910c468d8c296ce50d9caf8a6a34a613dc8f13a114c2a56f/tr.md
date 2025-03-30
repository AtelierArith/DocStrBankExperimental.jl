```
axpby!(α, x::AbstractArray, β, y::AbstractArray)
```

`y`'yi `x * α + y * β` ile üzerine yazın ve `y`'yi döndürün. `x` ve `y` aynı eksenlere sahipse, bu `y .= x .* a .+ y .* β` ile eşdeğerdir.

# Örnekler

```jldoctest
julia> x = [1; 2; 3];

julia> y = [4; 5; 6];

julia> axpby!(2, x, 2, y)
3-element Vector{Int64}:
 10
 14
 18
```
