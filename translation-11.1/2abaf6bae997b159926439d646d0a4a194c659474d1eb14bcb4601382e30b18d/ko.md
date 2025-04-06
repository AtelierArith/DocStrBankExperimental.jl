```
cis(x)
```

오일러의 공식을 사용하여 `exp(im*x)`보다 더 효율적인 방법: $\cos(x) + i \sin(x) = \exp(i x)$.

또한 [`cispi`](@ref), [`sincos`](@ref), [`exp`](@ref), [`angle`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> cis(π) ≈ -1
true
```
