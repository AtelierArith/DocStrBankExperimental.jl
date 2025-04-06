```
Meta.isexpr(ex, head[, n])::Bool
```

如果 `ex` 是具有给定类型 `head` 的 `Expr`，并且可选地参数列表的长度为 `n`，则返回 `true`。`head` 可以是一个 `Symbol` 或 `Symbol` 的集合。例如，要检查一个宏是否传递了一个函数调用表达式，可以使用 `isexpr(ex, :call)`。

# 示例

```jldoctest
julia> ex = :(f(x))
:(f(x))

julia> Meta.isexpr(ex, :block)
false

julia> Meta.isexpr(ex, :call)
true

julia> Meta.isexpr(ex, [:block, :call]) # 多个可能的头
true

julia> Meta.isexpr(ex, :call, 1)
false

julia> Meta.isexpr(ex, :call, 2)
true
```
