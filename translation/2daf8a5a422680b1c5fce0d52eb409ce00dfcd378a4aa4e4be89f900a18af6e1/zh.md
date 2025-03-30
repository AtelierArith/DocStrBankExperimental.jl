```
CFunction 结构体
```

用于处理从 `@cfunction` 返回值的垃圾回收句柄，当第一个参数用 '$' 注释时。像所有 `cfunction` 句柄一样，它应该作为 `Ptr{Cvoid}` 传递给 `ccall`，并将在调用点自动转换为适当的类型。

请参见 [`@cfunction`](@ref)。
