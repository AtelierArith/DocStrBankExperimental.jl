```
cconvert(T,x)
```

将 `x` 转换为可以作为类型 `T` 传递给 C 代码的值，通常通过调用 `convert(T, x)` 实现。

在 `x` 不能安全地转换为 `T` 的情况下，与 [`convert`](@ref) 不同，`cconvert` 可能返回一个与 `T` 不同类型的对象，但该对象适合由 [`unsafe_convert`](@ref) 处理。此函数的结果在 [`unsafe_convert`](@ref) 不再需要之前应保持有效（以便于 GC）。这可以用于分配将被 `ccall` 访问的内存。如果需要分配多个对象，可以将这些对象的元组用作返回值。

`convert` 和 `cconvert` 都不应将 Julia 对象转换为 `Ptr`。
