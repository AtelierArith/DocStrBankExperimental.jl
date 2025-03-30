```
frexp(val)
```

`x`의 크기가 $[1/2, 1)$ 또는 0인 `(x, exp)`를 반환하며, `val`은 `x \times 2^{exp}`와 같습니다.

자세한 내용은 [`significand`](@ref), [`exponent`](@ref), [`ldexp`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> frexp(6.0)
(0.75, 3)

julia> significand(6.0), exponent(6.0)  # 구간 [1, 2) 대신
(1.5, 2)

julia> frexp(0.0), frexp(NaN), frexp(-Inf)  # 지수는 오류를 발생시킴
((0.0, 0), (NaN, 0), (-Inf, 0))
```
