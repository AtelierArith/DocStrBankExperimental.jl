```
put(pair) -> f(n)
```

[`put`](@ref) の遅延カリー化バージョンです。

### 例

```jldoctest; setup=:(using Yao)
julia> put(1=>X)
(n -> put(n, 1 => X))
```
