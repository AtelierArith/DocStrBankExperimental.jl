```
ArgWrite = Union{AbstractString, AbstractCmd, IO}
```

`ArgWrite` 类型是一个联合类型，包含 `arg_write` 函数知道如何转换为可写的 IO 句柄的类型，除了 `Nothing`，`arg_write` 通过生成临时文件来处理 `Nothing`。有关详细信息，请参见 [`arg_write`](@ref)。
