```
isunaryoperator(s::Symbol)
```

如果符号可以用作一元（前缀）运算符，则返回 `true`，否则返回 `false`。

# 示例

```jldoctest
julia> Meta.isunaryoperator(:-), Meta.isunaryoperator(:√), Meta.isunaryoperator(:f)
(true, true, false)
```
