```
read(io::IO, T)
```

从 `io` 中读取一个类型为 `T` 的单个值，采用规范的二进制表示。

请注意，Julia 不会为您转换字节序。请使用 [`ntoh`](@ref) 或 [`ltoh`](@ref) 来实现此目的。

```
read(io::IO, String)
```

将 `io` 的全部内容读取为 `String`（另见 [`readchomp`](@ref)）。

# 示例

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> read(io, Char)
'J': ASCII/Unicode U+004A (category Lu: Letter, uppercase)

julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> read(io, String)
"JuliaLang is a GitHub organization"
```
