```
:expr
```

引用一个表达式 `expr`，返回 `expr` 的抽象语法树 (AST)。AST 可能是 `Expr`、`Symbol` 或一个字面值。语法 `:identifier` 计算为一个 `Symbol`。

另请参见: [`Expr`](@ref), [`Symbol`](@ref), [`Meta.parse`](@ref)

# 示例

```jldoctest
julia> expr = :(a = b + 2*x)
:(a = b + 2x)

julia> sym = :some_identifier
:some_identifier

julia> value = :0xff
0xff

julia> typeof((expr, sym, value))
Tuple{Expr, Symbol, UInt8}
```
