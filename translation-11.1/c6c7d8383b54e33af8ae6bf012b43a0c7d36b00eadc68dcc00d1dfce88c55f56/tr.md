```
⊊(a, b) -> Bool
⊋(b, a) -> Bool
```

`a`'n `b`'ye eşit olmayan bir alt kümesi olup olmadığını belirler.

Ayrıca bkz. [`issubset`](@ref) (`⊆`), [`⊈`](@ref).

# Örnekler

```jldoctest
julia> (1, 2) ⊊ (1, 2, 3)
true

julia> (1, 2) ⊊ (1, 2)
false
```
