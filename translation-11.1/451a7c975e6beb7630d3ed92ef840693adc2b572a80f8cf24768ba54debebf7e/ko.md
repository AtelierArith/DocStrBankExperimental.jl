```
axes(A)
```

배열 `A`에 대한 유효한 인덱스의 튜플을 반환합니다.

참고: [`size`](@ref), [`keys`](@ref), [`eachindex`](@ref).

# 예제

```jldoctest
julia> A = fill(1, (5,6,7));

julia> axes(A)
(Base.OneTo(5), Base.OneTo(6), Base.OneTo(7))
```
