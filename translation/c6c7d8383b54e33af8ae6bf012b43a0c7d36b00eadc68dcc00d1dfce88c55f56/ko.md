```
⊊(a, b) -> Bool
⊋(b, a) -> Bool
```

`a`가 `b`의 부분집합이지만 같지 않은지를 결정합니다.

또한 [`issubset`](@ref) (`⊆`), [`⊈`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> (1, 2) ⊊ (1, 2, 3)
true

julia> (1, 2) ⊊ (1, 2)
false
```
