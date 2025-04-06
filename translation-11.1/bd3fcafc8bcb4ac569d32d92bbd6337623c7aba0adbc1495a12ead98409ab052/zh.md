```
Expr(head::Symbol, args...)
```

一个表示解析的 Julia 代码（ASTs）中复合表达式的类型。每个表达式由一个 `head` `Symbol` 组成，用于标识它是哪种类型的表达式（例如，调用、for 循环、条件语句等），以及子表达式（例如，调用的参数）。子表达式存储在一个名为 `args` 的 `Vector{Any}` 字段中。

请参阅手册章节 [元编程](@ref) 和开发者文档 [Julia ASTs](@ref)。

# 示例

```jldoctest
julia> Expr(:call, :+, 1, 2)
:(1 + 2)

julia> dump(:(a ? b : c))
Expr
  head: Symbol if
  args: Array{Any}((3,))
    1: Symbol a
    2: Symbol b
    3: Symbol c
```
