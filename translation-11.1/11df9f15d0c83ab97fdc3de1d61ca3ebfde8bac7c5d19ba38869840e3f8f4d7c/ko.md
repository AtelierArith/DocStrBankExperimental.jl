```
NTuple{N, T}
```

길이가 `N`인 튜플의 타입을 나타내는 간결한 방법으로, 모든 요소는 타입 `T`입니다.

# 예시

```jldoctest
julia> isa((1, 2, 3, 4, 5, 6), NTuple{6, Int})
true
```

또한 [`ntuple`](@ref)를 참조하세요.
