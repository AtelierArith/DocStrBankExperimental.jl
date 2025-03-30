```
⊈(a, b) -> Bool
⊉(b, a) -> Bool
```

`⊆` 和 `⊇` 的否定，即检查 `a` 不是 `b` 的子集。

另见 [`issubset`](@ref) (`⊆`), [`⊊`](@ref).

# 示例

```jldoctest
julia> (1, 2) ⊈ (2, 3)
true

julia> (1, 2) ⊈ (1, 2, 3)
false
```
