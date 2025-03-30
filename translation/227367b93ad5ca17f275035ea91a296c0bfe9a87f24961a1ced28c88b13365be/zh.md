```
minimum(itr; [init])
```

返回集合中的最小元素。

对于空的 `itr`，返回的值可以通过 `init` 指定。它必须是 `min` 的中性元素（即大于或等于任何其他元素），因为未指定 `init` 是否用于非空集合。

!!! compat "Julia 1.6"
    关键字参数 `init` 需要 Julia 1.6 或更高版本。


# 示例

```jldoctest
julia> minimum(-20.5:10)
-20.5

julia> minimum([1,2,3])
1

julia> minimum([])
ERROR: ArgumentError: reducing over an empty collection is not allowed; consider supplying `init` to the reducer
Stacktrace:
[...]

julia> minimum([]; init=Inf)
Inf
```
