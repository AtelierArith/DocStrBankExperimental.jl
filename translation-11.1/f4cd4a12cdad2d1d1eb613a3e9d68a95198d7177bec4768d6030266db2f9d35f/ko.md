```
⊈(a, b) -> Bool
⊉(b, a) -> Bool
```

`⊆` 및 `⊇`의 부정, 즉 `a`가 `b`의 부분집합이 아님을 확인합니다.

자세한 내용은 [`issubset`](@ref) (`⊆`), [`⊊`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> (1, 2) ⊈ (2, 3)
true

julia> (1, 2) ⊈ (1, 2, 3)
false
```
