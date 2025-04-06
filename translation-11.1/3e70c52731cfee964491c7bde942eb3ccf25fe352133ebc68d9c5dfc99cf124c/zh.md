```
 isidentifier(s) -> Bool
```

返回符号或字符串 `s` 是否包含在 Julia 代码中解析为有效普通标识符（不是二元/一元运算符）的字符；另见 [`Base.isoperator`](@ref)。

在内部，Julia 允许 `Symbol` 中的任何字符序列（除了 `\0`），并且宏自动使用包含 `#` 的变量名，以避免与周围代码的命名冲突。为了让解析器识别变量，它使用有限的字符集（通过 Unicode 大大扩展）。`isidentifier()` 使得可以直接查询解析器某个符号是否包含有效字符。

# 示例

```jldoctest
julia> Meta.isidentifier(:x), Meta.isidentifier("1x")
(true, false)
```
