```
show([io::IO = stdout], x)
```

将值 `x` 的文本表示写入输出流 `io`。新类型 `T` 应重载 `show(io::IO, x::T)`。`show` 使用的表示通常包括特定于 Julia 的格式和类型信息，并且在可能的情况下应可解析为 Julia 代码。

[`repr`](@ref) 返回 `show` 的输出作为字符串。

对于类型 `T` 的对象，若要获得更详细的人类可读文本输出，请另外定义 `show(io::IO, ::MIME"text/plain", ::T)`。建议在此类方法中检查 `io` 的 `:compact` [`IOContext`](@ref) 键（通常检查为 `get(io, :compact, false)::Bool`），因为某些容器通过调用此方法并传递 `:compact => true` 来显示其元素。

另请参见 [`print`](@ref)，它写入未修饰的表示。

# 示例

```jldoctest
julia> show("Hello World!")
"Hello World!"
julia> print("Hello World!")
Hello World!
```
