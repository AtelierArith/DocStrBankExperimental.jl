```
typemax(T)
```

주어진 (실수) 숫자 `DataType`이 표현할 수 있는 가장 높은 값입니다.

참고: [`floatmax`](@ref), [`typemin`](@ref), [`eps`](@ref).

# 예제

```jldoctest
julia> typemax(Int8)
127

julia> typemax(UInt32)
0xffffffff

julia> typemax(Float64)
Inf

julia> typemax(Float32)
Inf32

julia> floatmax(Float32)  # 가장 큰 유한한 Float32 부동 소수점 숫자
3.4028235f38
```
