```
*(s::Union{AbstractString, AbstractChar}, t::Union{AbstractString, AbstractChar}...) -> AbstractString
```

连接字符串和/或字符，生成一个 [`String`](@ref) 或 [`AnnotatedString`](@ref)（视情况而定）。这相当于对参数调用 [`string`](@ref) 或 [`annotatedstring`](@ref) 函数。内置字符串类型的连接总是产生类型为 `String` 的值，但其他字符串类型可能会选择返回适当的不同类型的字符串。

# 示例

```jldoctest
julia> "Hello " * "world"
"Hello world"

julia> 'j' * "ulia"
"julia"
```
