```
@inbounds(blk)
```

消除表达式中的数组边界检查。

在下面的示例中，跳过对数组 `A` 的元素 `i` 的范围检查以提高性能。

```julia
function sum(A::AbstractArray)
    r = zero(eltype(A))
    for i in eachindex(A)
        @inbounds r += A[i]
    end
    return r
end
```

!!! warning
    使用 `@inbounds` 可能会对越界索引返回不正确的结果/崩溃/损坏。用户有责任手动检查。仅在从本地可用信息中确定所有访问都在边界内时使用 `@inbounds`。特别是，在像上面这样的函数中使用 `1:length(A)` 而不是 `eachindex(A)` 是 *不* 安全的，因为 `A` 的第一个索引对于所有子类型 `AbstractArray` 的用户定义类型可能不是 `1`。

