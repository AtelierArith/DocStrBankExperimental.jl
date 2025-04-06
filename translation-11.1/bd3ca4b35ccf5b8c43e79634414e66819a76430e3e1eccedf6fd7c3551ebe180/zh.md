```
@MIME_str
```

一个方便的宏，用于编写 [`MIME`](@ref) 类型，通常在向 [`show`](@ref) 添加方法时使用。例如，语法 `show(io::IO, ::MIME"text/html", x::MyType) = ...` 可用于定义如何写出 `MyType` 的 HTML 表示。
