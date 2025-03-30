```
\(x, y)
```

Sol bölme operatörü: `y`'nin sol tarafında `x`'in tersinin çarpımı. Tam sayı argümanları için kayan nokta sonuçları verir.

# Örnekler

```jldoctest
julia> 3 \ 6
2.0

julia> inv(3) * 6
2.0

julia> A = [4 3; 2 1]; x = [5, 6];

julia> A \ x
2-element Vector{Float64}:
  6.5
 -7.0

julia> inv(A) * x
2-element Vector{Float64}:
  6.5
 -7.0
```
