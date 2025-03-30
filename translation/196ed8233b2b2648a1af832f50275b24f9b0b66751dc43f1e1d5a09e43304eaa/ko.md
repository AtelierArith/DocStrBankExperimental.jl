```
typejoin(T, S, ...)
```

타입 `T`와 `S`의 가장 가까운 공통 조상을 반환합니다. 즉, 두 타입이 모두 상속하는 가장 좁은 타입입니다. 추가적인 varargs에 대해 재귀적으로 호출합니다.

# 예시

```jldoctest
julia> typejoin(Int, Float64)
Real

julia> typejoin(Int, Float64, ComplexF32)
Number
```
