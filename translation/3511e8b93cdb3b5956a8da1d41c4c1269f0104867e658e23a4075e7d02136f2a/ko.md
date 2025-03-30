```
vect(X...)
```

주어진 인수 목록을 포함하는 `promote_typeof`에서 계산된 요소 유형으로 [`Vector`](@ref)를 생성합니다.

# 예제

```jldoctest
julia> a = Base.vect(UInt8(1), 2.5, 1//2)
3-element Vector{Float64}:
 1.0
 2.5
 0.5
```
