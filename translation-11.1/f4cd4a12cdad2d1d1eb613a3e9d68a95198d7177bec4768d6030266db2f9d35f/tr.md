```
⊈(a, b) -> Bool
⊉(b, a) -> Bool
```

`⊆` ve `⊇`'nin olumsuzlaması, yani `a`'nın `b`'nin alt kümesi olmadığını kontrol eder.

Ayrıca bkz. [`issubset`](@ref) (`⊆`), [`⊊`](@ref).

# Örnekler

```jldoctest
julia> (1, 2) ⊈ (2, 3)
true

julia> (1, 2) ⊈ (1, 2, 3)
false
```
