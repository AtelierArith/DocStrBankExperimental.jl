```
axpy!(α, x::AbstractArray, y::AbstractArray)
```

Überschreibe `y` mit `x * α + y` und gebe `y` zurück. Wenn `x` und `y` die gleichen Achsen haben, ist es äquivalent zu `y .+= x .* a`.

# Beispiele

```jldoctest
julia> x = [1; 2; 3];

julia> y = [4; 5; 6];

julia> axpy!(2, x, y)
3-element Vector{Int64}:
  6
  9
 12
```
