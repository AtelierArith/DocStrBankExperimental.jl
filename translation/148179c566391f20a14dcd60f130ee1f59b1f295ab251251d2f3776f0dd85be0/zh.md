```
Printf.Format(format_str)
```

创建一个与 C printf 兼容的格式对象，可用于格式化值。

输入的 `format_str` 可以包含任何有效的格式说明符字符和修饰符。

`Format` 对象可以传递给 `Printf.format(f::Format, args...)` 以生成格式化字符串，或传递给 `Printf.format(io::IO, f::Format, args...)` 以直接将格式化字符串打印到 `io`。

为了方便，可以使用 `Printf.format"..."` 字符串宏形式在宏扩展时构建 `Printf.Format` 对象。

!!! compat "Julia 1.6"
    `Printf.Format` 需要 Julia 1.6 或更高版本。

