```
nextpow(a, x)
```

`x`보다 작지 않은 가장 작은 `a^n`으로, 여기서 `n`은 비부호 정수입니다. `a`는 1보다 커야 하고, `x`는 0보다 커야 합니다.

자세한 내용은 [`prevpow`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> nextpow(2, 7)
8

julia> nextpow(2, 9)
16

julia> nextpow(5, 20)
25

julia> nextpow(4, 16)
16
```
