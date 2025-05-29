```
content(x) -> block
```

`x`の内容を返します。これは、ブロックを返す[`AbstractContainer`](@ref)の特定のAPIです。

### 例

```jldoctest; setup=:(using Yao)
julia> content(2.0 * X)
X
```
