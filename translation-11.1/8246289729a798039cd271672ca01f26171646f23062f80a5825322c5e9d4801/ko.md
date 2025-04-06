```
inv(x)
```

`x`의 곱셈 역수를 반환합니다. 여기서 `x*inv(x)` 또는 `inv(x)*x`는 반올림 오차를 제외하고 [`one(x)`](@ref) (곱셈 항등원)을 생성합니다.

`x`가 숫자인 경우, 이는 본질적으로 `one(x)/x`와 동일하지만, 일부 유형의 경우 `inv(x)`가 약간 더 효율적일 수 있습니다.

# 예제

```jldoctest
julia> inv(2)
0.5

julia> inv(1 + 2im)
0.2 - 0.4im

julia> inv(1 + 2im) * (1 + 2im)
1.0 + 0.0im

julia> inv(2//3)
3//2
```

!!! compat "Julia 1.2"
    `inv(::Missing)`는 최소한 Julia 1.2가 필요합니다.

