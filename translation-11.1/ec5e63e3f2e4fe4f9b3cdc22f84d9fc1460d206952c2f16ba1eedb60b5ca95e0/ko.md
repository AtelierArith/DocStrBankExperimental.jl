```
ldexp(x, n)
```

$$
x \times 2^n
$$

를 계산합니다.

자세한 내용은 [`frexp`](@ref), [`exponent`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> ldexp(5.0, 2)
20.0
```
