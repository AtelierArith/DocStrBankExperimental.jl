```
Meta.quot(ex)::Expr
```

将表达式 `ex` 引用以生成一个头为 `quote` 的表达式。这可以用于表示 AST 中的 `Expr` 类型的对象。另请参阅关于 [QuoteNode](@ref man-quote-node) 的手册部分。

# 示例

```jldoctest
julia> eval(Meta.quot(:x))
:x

julia> dump(Meta.quot(:x))
Expr
  head: Symbol quote
  args: Array{Any}((1,))
    1: Symbol x

julia> eval(Meta.quot(:(1+2)))
:(1 + 2)
```
