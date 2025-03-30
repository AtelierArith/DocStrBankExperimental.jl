```
InexactError(name::Symbol, T, val)
```

无法将 `val` 精确转换为类型 `T`，在函数 `name` 的一个方法中。

# 示例

```jldoctest
julia> convert(Float64, 1+2im)
ERROR: InexactError: Float64(1 + 2im)
Stacktrace:
[...]
```
