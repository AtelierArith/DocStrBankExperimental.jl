```
unsafe_swap!(p::Ptr{T}, x, [order::Symbol])
```

这些操作原子性地执行，以同时获取和设置内存地址。如果硬件支持，这可能会优化为适当的硬件指令，否则其执行将类似于：

```
y = unsafe_load(p)
unsafe_store!(p, x)
return y
```

此函数的 `unsafe` 前缀表示不会对指针 `p` 进行验证以确保其有效性。与 C 一样，程序员有责任确保在调用此函数时引用的内存未被释放或垃圾回收。不正确的使用可能会导致程序段错误。

!!! compat "Julia 1.10"
    此函数至少需要 Julia 1.10。


另请参见：[`swapproperty!`](@ref Base.swapproperty!), [`atomic`](@ref)
