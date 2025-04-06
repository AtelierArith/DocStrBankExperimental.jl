```
println([io::IO], xs...)
```

将 `xs` 打印到 `io`，后面跟一个换行符（使用 [`print`](@ref)）。如果未提供 `io`，则打印到默认输出流 [`stdout`](@ref)。

另请参见 [`printstyled`](@ref) 以添加颜色等。

# 示例

```jldoctest
julia> println("Hello, world")
Hello, world

julia> io = IOBuffer();

julia> println(io, "Hello", ',', " world.")

julia> String(take!(io))
"Hello, world.\n"
```
