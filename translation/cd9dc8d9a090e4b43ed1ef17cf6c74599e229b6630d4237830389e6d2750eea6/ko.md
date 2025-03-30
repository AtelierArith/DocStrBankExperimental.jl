```
floatmin(T = Float64)
```

부동 소수점 타입 `T`로 표현 가능한 가장 작은 양의 정상 숫자를 반환합니다.

# 예제

```jldoctest
julia> floatmin(Float16)
Float16(6.104e-5)

julia> floatmin(Float32)
1.1754944f-38

julia> floatmin()
2.2250738585072014e-308
```
