```
show(io::IO, mime, x)
```

[`display`](@ref) 函数最终调用 `show`，以便将对象 `x` 作为给定的 `mime` 类型写入给定的 I/O 流 `io`（通常是内存缓冲区），如果可能的话。为了提供用户定义类型 `T` 的丰富多媒体表示，只需通过以下方式为 `T` 定义一个新的 `show` 方法：`show(io, ::MIME"mime", x::T) = ...`，其中 `mime` 是一个 MIME 类型字符串，函数体调用 [`write`](@ref)（或类似的）将 `x` 的表示写入 `io`。（请注意，`MIME""` 语法仅支持字面字符串；要以更灵活的方式构造 `MIME` 类型，请使用 `MIME{Symbol("")}`。）

例如，如果您定义了一个 `MyImage` 类型并知道如何将其写入 PNG 文件，您可以定义一个函数 `show(io, ::MIME"image/png", x::MyImage) = ...`，以允许您的图像在任何支持 PNG 的 `AbstractDisplay`（例如 IJulia）上显示。像往常一样，请确保 `import Base.show` 以便为内置的 Julia 函数 `show` 添加新方法。

从技术上讲，`MIME"mime"` 宏为给定的 `mime` 字符串定义了一个单例类型，这使我们能够利用 Julia 的调度机制来确定如何显示任何给定类型的对象。

默认的 MIME 类型是 `MIME"text/plain"`。对于 `text/plain` 输出，有一个后备定义，它调用带有 2 个参数的 `show`，因此并不总是需要为该情况添加方法。不过，如果某个类型受益于自定义的人类可读输出，则应定义 `show(::IO, ::MIME"text/plain", ::T)`。例如，`Day` 类型使用 `1 day` 作为 `text/plain` MIME 类型的输出，而 `Day(1)` 作为 2 个参数 `show` 的输出。

# 示例

```jldoctest
julia> struct Day
           n::Int
       end

julia> Base.show(io::IO, ::MIME"text/plain", d::Day) = print(io, d.n, " day")

julia> Day(1)
1 day
```

容器类型通常通过对元素 `x` 调用 `show(io, MIME"text/plain"(), x)` 来实现 3 个参数的 `show`，并在作为第一个参数传递的 [`IOContext`](@ref) 中设置 `:compact => true`。
