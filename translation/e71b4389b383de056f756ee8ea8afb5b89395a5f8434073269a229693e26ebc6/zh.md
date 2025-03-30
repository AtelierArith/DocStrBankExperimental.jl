```
@view A[inds...]
```

将索引表达式 `A[inds...]` 转换为等效的 [`view`](@ref) 调用。

这只能直接应用于单个索引表达式，并且对于包含特殊 `begin` 或 `end` 索引语法的表达式（如 `A[begin, 2:end-1]`，因为这些在正常的 [`view`](@ref) 函数中不受支持）特别有帮助。

请注意，`@view` 不能用作常规赋值的目标（例如，`@view(A[1, 2:end]) = ...`），未装饰的 [索引赋值](@ref man-indexed-assignment)（`A[1, 2:end] = ...`）或广播索引赋值（`A[1, 2:end] .= ...`）也不会复制。然而，它对于 *更新* 广播赋值是有用的，例如 `@view(A[1, 2:end]) .+= 1`，因为这是 `@view(A[1, 2:end]) .= @view(A[1, 2:end]) + 1` 的简单语法，而右侧的索引表达式在没有 `@view` 的情况下会复制。

另见 [`@views`](@ref) 以将整个代码块切换为使用视图进行非标量索引。

!!! compat "Julia 1.5"
    在索引表达式中使用 `begin` 来引用第一个索引需要至少 Julia 1.5。


# 示例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> b = @view A[:, 1]
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3

julia> fill!(b, 0)
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 0
 0

julia> A
2×2 Matrix{Int64}:
 0  2
 0  4
```
