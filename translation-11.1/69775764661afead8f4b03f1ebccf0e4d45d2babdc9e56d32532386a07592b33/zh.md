```
minimum(f, itr; [init])
```

返回对 `itr` 中每个元素调用函数 `f` 的最小结果。

对于空的 `itr`，返回的值可以通过 `init` 指定。它必须是 `min` 的中性元素（即大于或等于任何其他元素），因为未指定 `init` 是否用于非空集合。

!!! compat "Julia 1.6"
    关键字参数 `init` 需要 Julia 1.6 或更高版本。


# 示例

```jldoctest
julia> minimum(length, ["Julion", "Julia", "Jule"])
4

julia> minimum(length, []; init=typemax(Int64))
9223372036854775807

julia> minimum(sin, Real[]; init=1.0)  # 好，因为 sin 的输出 <= 1
1.0
```
