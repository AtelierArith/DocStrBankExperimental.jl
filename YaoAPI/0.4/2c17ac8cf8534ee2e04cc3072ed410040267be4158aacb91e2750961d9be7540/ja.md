```
nparameters(block) -> Int
```

`block`内のパラメータの数を返します。 [`niparams`](@ref)も参照してください。

### 例

```jldoctest; setup=:(using Yao)
julia> nparameters(chain(Rx(0.1), Rz(0.2)))
2
```
