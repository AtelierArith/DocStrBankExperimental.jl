```
getiparams(block)
```

ノード `block` の内因的パラメータを返します。デフォルトは空のタプルです。

### 例

```jldoctest; setup=:(using Yao)
julia> getiparams(Rx(0.1))
0.1
```
