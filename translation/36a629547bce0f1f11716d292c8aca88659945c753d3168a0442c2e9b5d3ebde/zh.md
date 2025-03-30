```
print([io::IO], xs...)
```

将文本的规范（未修饰）表示写入 `io`（如果未给出 `io`，则写入默认输出流 [`stdout`](@ref)）。`print` 使用的表示包括最小格式，并尽量避免 Julia 特有的细节。

`print` 会回退到调用 `show`，因此大多数类型只需定义 `show`。如果您的类型有单独的“普通”表示，请定义 `print`。例如，`show` 用引号显示字符串，而 `print` 则不使用引号显示字符串。

另请参见 [`println`](@ref)、[`string`](@ref)、[`printstyled`](@ref)。

# 示例

```jldoctest
julia> print("Hello World!")
Hello World!
julia> io = IOBuffer();

julia> print(io, "Hello", ' ', :World!)

julia> String(take!(io))
"Hello World!"
```
