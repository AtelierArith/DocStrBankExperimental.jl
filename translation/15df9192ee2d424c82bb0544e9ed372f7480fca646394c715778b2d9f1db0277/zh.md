```
unsafe_replace!(p::Ptr{T}, expected, desired,
               [success_order::Symbol[, fail_order::Symbol=success_order]]) -> (; old, success::Bool)
```

这些操作原子地执行以获取并有条件地将内存地址设置为给定值。如果硬件支持，这可能会优化为适当的硬件指令，否则其执行将类似于：

```
y = unsafe_load(p, fail_order)
ok = y === expected
if ok
    unsafe_store!(p, desired, success_order)
end
return (; old = y, success = ok)
```

此函数的 `unsafe` 前缀表示不会对指针 `p` 进行验证以确保其有效性。与 C 一样，程序员有责任确保在调用此函数时引用的内存未被释放或垃圾回收。不正确的使用可能会导致程序段错误。

!!! compat "Julia 1.10"
    此函数至少需要 Julia 1.10。


另请参见: [`replaceproperty!`](@ref Base.replaceproperty!), [`atomic`](@ref)
