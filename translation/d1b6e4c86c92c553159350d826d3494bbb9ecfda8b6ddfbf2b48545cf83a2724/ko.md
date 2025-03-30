```
signed(T::Integer)
```

정수 비트 유형을 동일한 크기의 부호 있는 유형으로 변환합니다.

# 예제

```jldoctest
julia> signed(UInt16)
Int16
julia> signed(UInt64)
Int64
```
