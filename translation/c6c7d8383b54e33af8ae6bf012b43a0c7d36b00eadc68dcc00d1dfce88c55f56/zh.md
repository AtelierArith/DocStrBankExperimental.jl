```
⊊(a, b) -> Bool
⊋(b, a) -> Bool
```

确定 `a` 是否是 `b` 的子集，但不等于 `b`。

另见 [`issubset`](@ref) (`⊆`), [`⊈`](@ref)。

# 示例

```jldoctest
julia> (1, 2) ⊊ (1, 2, 3)
true

julia> (1, 2) ⊊ (1, 2)
false
```
