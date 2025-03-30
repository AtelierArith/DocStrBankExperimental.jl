```
endswith(suffix)
```

创建一个函数，检查其参数是否以 `suffix` 结尾，即一个等价于 `y -> endswith(y, suffix)` 的函数。

返回的函数类型为 `Base.Fix2{typeof(endswith)}`，可用于实现专门的方法。

!!! compat "Julia 1.5"
    单个参数 `endswith(suffix)` 至少需要 Julia 1.5。


# 示例

```jldoctest
julia> endswith("Julia")("Ends with Julia")
true

julia> endswith("Julia")("JuliaLang")
false
```
