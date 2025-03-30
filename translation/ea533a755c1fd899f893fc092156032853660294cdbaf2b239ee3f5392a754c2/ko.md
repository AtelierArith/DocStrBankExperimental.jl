```
floatmax(T = Float64)
```

부동 소수점 타입 `T`로 표현할 수 있는 가장 큰 유한 수를 반환합니다.

참고: [`typemax`](@ref), [`floatmin`](@ref), [`eps`](@ref).

# 예제

```jldoctest
julia> floatmax(Float16)
Float16(6.55e4)

julia> floatmax(Float32)
3.4028235f38

julia> floatmax()
1.7976931348623157e308

julia> typemax(Float64)
Inf
```
