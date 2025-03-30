```
float(x)
```

숫자 또는 배열을 부동 소수점 데이터 유형으로 변환합니다.

참고: [`complex`](@ref), [`oftype`](@ref), [`convert`](@ref).

# 예제

```jldoctest
julia> float(1:1000)
1.0:1.0:1000.0

julia> float(typemax(Int32))
2.147483647e9
```
