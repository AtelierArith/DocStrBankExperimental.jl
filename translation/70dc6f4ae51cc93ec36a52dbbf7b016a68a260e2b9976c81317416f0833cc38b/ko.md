```
Float64(x [, mode::RoundingMode])
```

`x`로부터 `Float64`를 생성합니다. `x`가 정확하게 표현될 수 없는 경우 `mode`가 `x`가 어떻게 반올림되는지를 결정합니다.

# 예제

```jldoctest
julia> Float64(pi, RoundDown)
3.141592653589793

julia> Float64(pi, RoundUp)
3.1415926535897936
```

사용 가능한 반올림 모드에 대한 내용은 [`RoundingMode`](@ref)를 참조하세요.
