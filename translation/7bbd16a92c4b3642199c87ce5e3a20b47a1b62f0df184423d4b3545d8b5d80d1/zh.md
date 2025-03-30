```
sprint(f::Function, args...; context=nothing, sizehint=0)
```

调用给定的函数，使用 I/O 流和提供的额外参数。写入此 I/O 流的所有内容将作为字符串返回。`context` 可以是一个 [`IOContext`](@ref)，其属性将被使用，也可以是一个指定属性及其值的 `Pair`，或者是一个指定多个属性及其值的 `Pair` 元组。`sizehint` 建议缓冲区的容量（以字节为单位）。

可选的关键字参数 `context` 可以设置为 `:key=>value` 对，`:key=>value` 对的元组，或者是一个 `IO` 或 [`IOContext`](@ref) 对象，其属性用于传递给 `f` 的 I/O 流。可选的 `sizehint` 是建议的大小（以字节为单位），用于分配写入字符串所用的缓冲区。

!!! compat "Julia 1.7"
    将元组传递给关键字 `context` 需要 Julia 1.7 或更高版本。


# 示例

```jldoctest
julia> sprint(show, 66.66666; context=:compact => true)
"66.6667"

julia> sprint(showerror, BoundsError([1], 100))
"BoundsError: attempt to access 1-element Vector{Int64} at index [100]"
```
