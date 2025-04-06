```
isbinaryoperator(s::Symbol)
```

如果符号可以用作二元（中缀）运算符，则返回 `true`，否则返回 `false`。

# 示例

```jldoctest
julia> Meta.isbinaryoperator(:-), Meta.isbinaryoperator(:√), Meta.isbinaryoperator(:f)
(true, false, false)
```
