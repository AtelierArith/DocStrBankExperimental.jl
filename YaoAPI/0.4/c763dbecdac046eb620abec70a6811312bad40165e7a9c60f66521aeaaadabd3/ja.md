```
occupied_locs(x)
```

`x`の占有されている位置のタプルを返します。

### 例

```jldoctest; setup=:(using Yao)
julia> occupied_locs(kron(5, 1=>X, 3=>X))
(1, 3)

julia> occupied_locs(kron(5, 1=>X, 3=>I2))
(1,)
```
