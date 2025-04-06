```
maximum(itr; [init])
```

返回集合中的最大元素。

对于空的 `itr`，返回的值可以通过 `init` 指定。它必须是 `max` 的中性元素（即小于或等于任何其他元素），因为未指定 `init` 是否用于非空集合。

!!! compat "Julia 1.6"
    关键字参数 `init` 需要 Julia 1.6 或更高版本。


# 示例

```jldoctest
julia> maximum(-20.5:10)
9.5

julia> maximum([1,2,3])
3

julia> maximum(())
ERROR: ArgumentError: reducing over an empty collection is not allowed; consider supplying `init` to the reducer
Stacktrace:
[...]

julia> maximum((); init=-Inf)
-Inf
```
