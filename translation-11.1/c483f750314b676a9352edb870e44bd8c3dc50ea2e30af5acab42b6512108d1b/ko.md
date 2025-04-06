```
typemin(T)
```

주어진 (실수) 숫자 데이터 타입 `T`로 표현할 수 있는 가장 낮은 값입니다.

참고: [`floatmin`](@ref), [`typemax`](@ref), [`eps`](@ref).

# 예제

```jldoctest
julia> typemin(Int8)
-128

julia> typemin(UInt32)
0x00000000

julia> typemin(Float16)
-Inf16

julia> typemin(Float32)
-Inf32

julia> nextfloat(-Inf32)  # 가장 작은 유한한 Float32 부동 소수점 수
-3.4028235f38
```
