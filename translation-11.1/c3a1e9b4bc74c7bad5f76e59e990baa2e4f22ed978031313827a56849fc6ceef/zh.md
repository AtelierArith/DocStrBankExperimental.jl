```
copy!(dst, src) -> dst
```

就地 [`copy`](@ref) 将 `src` 复制到 `dst`，丢弃 `dst` 中的任何现有元素。如果 `dst` 和 `src` 是相同类型，则在调用后应满足 `dst == src`。如果 `dst` 和 `src` 是多维数组，则它们必须具有相等的 [`axes`](@ref)。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


另请参见 [`copyto!`](@ref)。

!!! compat "Julia 1.1"
    此方法至少需要 Julia 1.1。在 Julia 1.0 中，此方法可通过 `Future` 标准库作为 `Future.copy!` 使用。

