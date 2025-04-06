```
Float32(x [, mode::RoundingMode])
```

`x`로부터 `Float32`를 생성합니다. `x`가 정확하게 표현될 수 없는 경우 `mode`가 `x`가 어떻게 반올림되는지를 결정합니다.

# 예제

```jldoctest
julia> Float32(1/3, RoundDown)
0.3333333f0

julia> Float32(1/3, RoundUp)
0.33333334f0
```

사용 가능한 반올림 모드에 대해서는 [`RoundingMode`](@ref)를 참조하세요.
