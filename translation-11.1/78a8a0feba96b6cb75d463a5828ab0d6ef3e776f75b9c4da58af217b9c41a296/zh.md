```
startswith(prefix)
```

创建一个函数，检查其参数是否以 `prefix` 开头，即一个等价于 `y -> startswith(y, prefix)` 的函数。

返回的函数类型为 `Base.Fix2{typeof(startswith)}`，可以用于实现专门的方法。

!!! compat "Julia 1.5"
    单个参数 `startswith(prefix)` 至少需要 Julia 1.5。


# 示例

```jldoctest
julia> startswith("Julia")("JuliaLang")
true

julia> startswith("Julia")("Ends with Julia")
false
```
