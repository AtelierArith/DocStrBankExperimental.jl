```
Vector{T}(undef, n)
```

길이 `n`의 초기화되지 않은 [`Vector{T}`](@ref)를 생성합니다.

# 예제

```julia-repl
julia> Vector{Float64}(undef, 3)
3-element Array{Float64, 1}:
 6.90966e-310
 6.90966e-310
 6.90966e-310
```
