```
isoperator(s::Symbol)
```

如果符号可以用作运算符，则返回 `true`，否则返回 `false`。

# 示例

```jldoctest
julia> Meta.isoperator(:+), Meta.isoperator(:f)
(true, false)
```
