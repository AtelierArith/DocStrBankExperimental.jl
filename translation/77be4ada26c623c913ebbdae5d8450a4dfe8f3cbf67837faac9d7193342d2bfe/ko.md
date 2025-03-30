```
exp(x)
```

`x`의 자연 밑 지수 함수를 계산합니다. 즉, $ℯ^x$입니다.

또한 [`exp2`](@ref), [`exp10`](@ref) 및 [`cis`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> exp(1.0)
2.718281828459045

julia> exp(im * pi) ≈ cis(pi)
true
```
