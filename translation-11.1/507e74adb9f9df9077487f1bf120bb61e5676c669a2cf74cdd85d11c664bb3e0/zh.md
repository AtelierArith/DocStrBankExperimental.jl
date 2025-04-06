```
ArgRead = Union{AbstractString, AbstractCmd, IO}
```

`ArgRead` 类型是一个联合类型，包含 `arg_read` 函数知道如何转换为可读的 IO 句柄的类型。有关详细信息，请参见 [`arg_read`](@ref)。
