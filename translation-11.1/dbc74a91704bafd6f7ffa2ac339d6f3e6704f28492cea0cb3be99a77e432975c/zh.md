```
unsafe_modify!(p::Ptr{T}, op, x, [order::Symbol]) -> Pair
```

这些操作原子地执行以获取和设置内存地址，应用函数 `op`。如果硬件支持（例如，原子递增），这可能会优化为适当的硬件指令，否则其执行将类似于：

```
y = unsafe_load(p)
z = op(y, x)
unsafe_store!(p, z)
return y => z
```

此函数的 `unsafe` 前缀表示不会对指针 `p` 进行验证以确保其有效性。与 C 一样，程序员有责任确保在调用此函数时引用的内存未被释放或垃圾回收。错误的使用可能会导致程序段错误。

!!! compat "Julia 1.10"
    此函数至少需要 Julia 1.10。


另请参见: [`modifyproperty!`](@ref Base.modifyproperty!), [`atomic`](@ref)
