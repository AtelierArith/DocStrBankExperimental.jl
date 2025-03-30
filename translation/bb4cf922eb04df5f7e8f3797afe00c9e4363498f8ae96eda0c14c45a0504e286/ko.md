```
Inf, Inf64
```

타입 [`Float64`](@ref)의 양의 무한대입니다.

참고: [`isfinite`](@ref), [`typemax`](@ref), [`NaN`](@ref), [`Inf32`](@ref).

# 예제

```jldoctest
julia> π/0
Inf

julia> +1.0 / -0.0
-Inf

julia> ℯ^-Inf
0.0
```
