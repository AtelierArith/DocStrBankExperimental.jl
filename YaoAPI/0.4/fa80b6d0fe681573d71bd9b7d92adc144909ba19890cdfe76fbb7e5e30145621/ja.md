```
niparam(block) -> Int
```

`block`内の内因性パラメータの数を返します。詳細は[`nparameters`](@ref)を参照してください。

### 例

```jldoctest; setup=:(using Yao)
julia> niparams(Rx(0.1))
1
```
