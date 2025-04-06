```
Regex(pattern[, flags]) <: AbstractPattern
```

一个表示正则表达式的类型。`Regex` 对象可以用于与 [`match`](@ref) 匹配字符串。

`Regex` 对象可以使用 [`@r_str`](@ref) 字符串宏创建。如果需要插入 `pattern` 字符串，通常使用 `Regex(pattern[, flags])` 构造函数。有关标志的详细信息，请参见字符串宏的文档。

!!! note
    要转义插入的变量，请使用 `\Q` 和 `\E`（例如 `Regex("\\Q$x\\E")`）

