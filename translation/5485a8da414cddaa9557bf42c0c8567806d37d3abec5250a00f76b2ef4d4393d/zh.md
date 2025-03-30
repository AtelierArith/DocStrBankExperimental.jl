```
repr(mime, x; context=nothing)
```

返回一个 `AbstractString` 或 `Vector{UInt8}`，包含以请求的 `mime` 类型表示的 `x`，如 [`show(io, mime, x)`](@ref) 所示（如果没有合适的 `show` 可用，则抛出 [`MethodError`](@ref)）。对于具有文本表示的 MIME 类型（例如 `"text/html"` 或 `"application/postscript"`），返回 `AbstractString`，而二进制数据则返回 `Vector{UInt8}`。（函数 `istextmime(mime)` 返回 Julia 是否将给定的 `mime` 类型视为文本。）

可选的关键字参数 `context` 可以设置为 `:key=>value` 对或一个 `IO` 或 [`IOContext`](@ref) 对象，其属性用于传递给 `show` 的 I/O 流。

作为特例，如果 `x` 是 `AbstractString`（对于文本 MIME 类型）或 `Vector{UInt8}`（对于二进制 MIME 类型），则 `repr` 函数假定 `x` 已经是请求的 `mime` 格式，并简单地返回 `x`。此特例不适用于 `"text/plain"` MIME 类型。这对于将原始数据传递给 `display(m::MIME, x)` 很有用。

特别地，`repr("text/plain", x)` 通常是为人类消费而设计的 `x` 的“美观打印”版本。另请参见 [`repr(x)`](@ref)，以返回一个字符串，对应于 [`show(x)`](@ref)，可能更接近于 `x` 的值在 Julia 中的输入方式。

# 示例

```jldoctest
julia> A = [1 2; 3 4];

julia> repr("text/plain", A)
"2×2 Matrix{Int64}:\n 1  2\n 3  4"
```
