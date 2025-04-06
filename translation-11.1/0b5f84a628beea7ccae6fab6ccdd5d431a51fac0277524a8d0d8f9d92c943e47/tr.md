```
axpy!(α, x::AbstractArray, y::AbstractArray)
```

`y`'yi `x * α + y` ile üzerine yazın ve `y`'yi döndürün. Eğer `x` ve `y` aynı eksenlere sahipse, bu `y .+= x .* a` ile eşdeğerdir.

# Örnekler

```jldoctest
julia> x = [1; 2; 3];

julia> y = [4; 5; 6];

julia> axpy!(2, x, y)
3-element Vector{Int64}:
  6
  9
 12
```
