```
unsafe_trunc(T, x)
```

타입 `T`의 절대값이 `x`의 절대값보다 작거나 같은 가장 가까운 정수 값을 반환합니다. 만약 그 값이 `T`로 표현할 수 없다면, 임의의 값이 반환됩니다. [`trunc`](@ref)도 참조하세요.

# 예제

```jldoctest
julia> unsafe_trunc(Int, -2.2)
-2

julia> unsafe_trunc(Int, NaN)
-9223372036854775808
```
