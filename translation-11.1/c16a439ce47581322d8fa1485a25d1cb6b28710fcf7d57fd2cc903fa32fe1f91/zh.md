```
display(x)
display(d::AbstractDisplay, x)
display(mime, x)
display(d::AbstractDisplay, mime, x)
```

使用显示栈中最上层的适用显示来显示 `x`，通常使用 `x` 支持的最丰富的多媒体输出，作为后备使用纯文本 [`stdout`](@ref) 输出。`display(d, x)` 变体尝试仅在给定的显示 `d` 上显示 `x`，如果 `d` 不能显示此类型的对象，则抛出 [`MethodError`](@ref)。

一般来说，您不能假设 `display` 输出会发送到 `stdout`（与 [`print(x)`](@ref) 或 [`show(x)`](@ref) 不同）。例如，`display(x)` 可能会打开一个单独的窗口显示图像。`display(x)` 的意思是“以您能为当前输出设备显示 `x` 的最佳方式。”如果您想要保证发送到 `stdout` 的类似 REPL 的文本输出，请使用 [`show(stdout, "text/plain", x)`](@ref)。

还有两个带有 `mime` 参数的变体（一个 MIME 类型字符串，例如 `"image/png"`），它们尝试仅使用请求的 MIME 类型显示 `x`，如果此类型不被显示（s）或 `x` 支持，则抛出 `MethodError`。使用这些变体，您还可以通过传递 `x::AbstractString`（对于具有基于文本存储的 MIME 类型，例如 text/html 或 application/postscript）或 `x::Vector{UInt8}`（对于二进制 MIME 类型）来提供请求的 MIME 类型的“原始”数据。

要自定义如何显示类型的实例，请重载 [`show`](@ref)，而不是 `display`，如手册中关于 [自定义美观打印](@ref man-custom-pretty-printing) 的部分所述。
