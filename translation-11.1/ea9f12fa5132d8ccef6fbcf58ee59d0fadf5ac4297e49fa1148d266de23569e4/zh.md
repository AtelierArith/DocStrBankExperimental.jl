```
unsafe_store!(p::Ptr{T}, x, i::Integer=1)
unsafe_store!(p::Ptr{T}, x, order::Symbol)
unsafe_store!(p::Ptr{T}, x, i::Integer, order::Symbol)
```

将类型为 `T` 的值存储到从 `p` 开始的第 `i` 个元素（1 索引）地址中。这相当于 C 表达式 `p[i-1] = x`。可以选择提供一个原子内存顺序。

此函数的 `unsafe` 前缀表示不会对指针 `p` 进行验证以确保其有效性。与 C 一样，程序员有责任确保在调用此函数时引用的内存未被释放或垃圾回收。错误的使用可能会导致程序段错误。与 C 不同的是，只要类型兼容，将不同类型分配的内存区域存储可能是有效的。

!!! compat "Julia 1.10"
    `order` 参数自 Julia 1.10 起可用。


另请参见: [`atomic`](@ref)
