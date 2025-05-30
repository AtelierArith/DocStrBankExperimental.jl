```
getiparams(block)
```

ノード `block` の固有パラメータを返します。デフォルトは空のタプルです。

### 例

```jldoctest; setup=:(using Yao)
julia> getiparams(Rx(0.1))
0.1
```
