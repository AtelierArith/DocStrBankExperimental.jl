```
oftype(x, y)
```

将 `y` 转换为 `x` 的类型，即 `convert(typeof(x), y)`。

# 示例

```jldoctest
julia> x = 4;

julia> y = 3.;

julia> oftype(x, y)
3

julia> oftype(y, x)
4.0
```
