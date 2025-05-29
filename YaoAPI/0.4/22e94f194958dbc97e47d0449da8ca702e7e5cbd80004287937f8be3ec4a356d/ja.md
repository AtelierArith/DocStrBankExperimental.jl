```
parameters(block)
```

指定されたルート `block` を持つブロックツリーに含まれるすべてのパラメータを返します。

### 例

```jldoctest; setup=:(using Yao)
julia> parameters(chain(Rx(0.1), Rz(0.2)))
2-element Vector{Float64}:
 0.1
 0.2
```
