```
zeros([T=Float64,] dims::Tuple)
zeros([T=Float64,] dims...)
```

`T` 타입의 요소를 가지며, `dims`로 지정된 크기의 모든 요소가 0인 `Array`를 생성합니다. [`fill`](@ref), [`ones`](@ref), [`zero`](@ref)도 참조하세요.

# 예제

```jldoctest
julia> zeros(1)
1-element Vector{Float64}:
 0.0

julia> zeros(Int8, 2, 3)
2×3 Matrix{Int8}:
 0  0  0
 0  0  0
```
