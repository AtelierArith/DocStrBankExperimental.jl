```
cglobal((symbol, library) [, type=Cvoid])
```

获取指向在 C 导出的共享库中的全局变量的指针，指定方式与 [`ccall`](@ref) 完全相同。如果未提供 `Type` 参数，则默认返回 `Ptr{Cvoid}`。可以通过 [`unsafe_load`](@ref) 或 [`unsafe_store!`](@ref) 分别读取或写入这些值。
