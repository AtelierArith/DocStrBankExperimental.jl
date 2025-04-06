```
now(::Type{UTC}) -> DateTime
```

사용자의 시스템 시간에 해당하는 `DateTime`을 UTC/GMT로 반환합니다. 다른 시간대에 대해서는 TimeZones.jl 패키지를 참조하세요.

# 예제

```julia
julia> now(UTC)
2023-01-04T10:52:24.864
```
