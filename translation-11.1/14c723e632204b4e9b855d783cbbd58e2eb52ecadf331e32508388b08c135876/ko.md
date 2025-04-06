```
tuple(xs...)
```

주어진 객체의 튜플을 생성합니다.

자세한 내용은 [`Tuple`](@ref), [`ntuple`](@ref), [`NamedTuple`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> tuple(1, 'b', pi)
(1, 'b', π)

julia> ans === (1, 'b', π)
true

julia> Tuple(Real[1, 2, pi])  # 컬렉션을 사용합니다
(1, 2, π)
```
