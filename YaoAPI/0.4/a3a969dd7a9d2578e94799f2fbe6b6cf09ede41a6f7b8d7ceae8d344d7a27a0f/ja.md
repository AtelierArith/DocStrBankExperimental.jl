```
probs(register) -> Vector
```

計算基底の確率分布、すなわち $|<x|ψ>|^2$ を返します。

### 例

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"101");

julia> reg |> probs
8-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
 0.0
 1.0
 0.0
 0.0
```
