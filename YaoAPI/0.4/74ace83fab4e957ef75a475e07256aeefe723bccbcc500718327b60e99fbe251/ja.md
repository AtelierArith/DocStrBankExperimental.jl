```
setiparams!(block, itr)
setiparams!(block, params...)
```

`block`のパラメータを設定します。

### 例

```jldoctest; setup=:(using Yao)
julia> setiparams!(Rx(0.1), 0.2)
rot(X, 0.2)
```
