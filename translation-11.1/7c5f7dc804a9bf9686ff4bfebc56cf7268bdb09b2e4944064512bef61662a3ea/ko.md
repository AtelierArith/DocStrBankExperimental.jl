```
cispi(x)
```

`cis(pi*x)`에 대한 더 정확한 방법 (특히 큰 `x`에 대해).

또한 [`cis`](@ref), [`sincospi`](@ref), [`exp`](@ref), [`angle`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> cispi(10000)
1.0 + 0.0im

julia> cispi(0.25 + 1im)
0.030556854645954562 + 0.03055685464595456im
```

!!! compat "Julia 1.6"
    이 함수는 Julia 1.6 이상이 필요합니다.

