```
list(tarball; [ strict = true ]) -> Vector{Header}
list(callback, tarball; [ strict = true ])

    callback  :: Header, [ <data> ] --> Any
    tarball   :: Union{AbstractString, AbstractCmd, IO}
    strict    :: Bool
```

列出位于路径 `tarball` 的 tar 归档（“tarball”）的内容。如果 `tarball` 是一个 IO 句柄，则从该流中读取 tar 内容。返回一个 `Header` 结构的向量。有关详细信息，请参见 [`Header`](@ref)。

如果提供了 `callback`，则在每个 `Header` 上调用该回调，而不是返回一个头部的向量。如果 tarball 中的项目数量很大，或者您想在 tarball 中出现错误之前检查项目，这可能会很有用。如果 `callback` 函数可以接受第二个参数，类型为 `Vector{UInt8}` 或 `Vector{Pair{Symbol, String}}`，则它将被调用，并以单个字节向量或将字段名称映射到该字段的原始数据的对的向量的形式表示原始头部数据（如果这些字段连接在一起，结果就是头部的原始数据）。

默认情况下，如果 `list` 遇到 `extract` 函数拒绝提取的任何 tarball 内容，则会出错。使用 `strict=false` 时，它将跳过这些检查，并列出 tar 文件的所有内容，无论 `extract` 是否会提取它们。请注意，恶意的 tarball 可以做各种巧妙和意想不到的事情，试图欺骗您做一些不好的事情。

如果 `tarball` 参数是一个骨架文件（请参见 `extract` 和 `create`），则 `list` 将从文件头检测到这一点，并适当地列出或迭代骨架文件的头部。
