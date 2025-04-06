```
prevpow(a, x)
```

`x`보다 크지 않은 가장 큰 `a^n`, 여기서 `n`은 0 이상의 정수입니다. `a`는 1보다 커야 하며, `x`는 1보다 작아서는 안 됩니다.

자세한 내용은 [`nextpow`](@ref), [`isqrt`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> prevpow(2, 7)
4

julia> prevpow(2, 9)
8

julia> prevpow(5, 20)
5

julia> prevpow(4, 16)
16
```
