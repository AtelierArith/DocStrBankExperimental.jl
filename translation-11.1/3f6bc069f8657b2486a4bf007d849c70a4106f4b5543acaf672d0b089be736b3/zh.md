```
repr(x; context=nothing)
```

使用 [`show`](@ref) 函数从任何值创建一个字符串。您不应向 `repr` 添加方法；而应定义一个 `show` 方法。

可选的关键字参数 `context` 可以设置为 `:key=>value` 对，`:key=>value` 对的元组，或一个 `IO` 或 [`IOContext`](@ref) 对象，其属性用于传递给 `show` 的 I/O 流。

请注意，`repr(x)` 通常与在 Julia 中输入 `x` 的值相似。另请参见 [`repr(MIME("text/plain"), x)`](@ref)，以返回一个更适合人类消费的 `x` 的“美观打印”版本，相当于 `x` 的 REPL 显示。

!!! compat "Julia 1.7"
    将元组传递给关键字 `context` 需要 Julia 1.7 或更高版本。


# 示例

```jldoctest
julia> repr(1)
"1"

julia> repr(zeros(3))
"[0.0, 0.0, 0.0]"

julia> repr(big(1/3))
"0.333333333333333314829616256247390992939472198486328125"

julia> repr(big(1/3), context=:compact => true)
"0.333333"
```
