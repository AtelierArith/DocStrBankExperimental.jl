```
filter(f)
```

함수를 생성하여 [`filter`](@ref) 함수를 사용하여 인수를 필터링합니다. 즉, `x -> filter(f, x)`와 동등한 함수입니다.

반환된 함수는 `Base.Fix1{typeof(filter)}` 유형이며, 이를 사용하여 특수화된 메서드를 구현할 수 있습니다.

# 예제

```jldoctest
julia> (1, 2, Inf, 4, NaN, 6) |> filter(isfinite)
(1, 2, 4, 6)

julia> map(filter(iseven), [1:3, 2:4, 3:5])
3-element Vector{Vector{Int64}}:
 [2]
 [2, 4]
 [4]
```

!!! compat "Julia 1.9"
    이 메서드는 최소한 Julia 1.9가 필요합니다.

