```
diagind(M::AbstractMatrix, k::Integer = 0, indstyle::IndexStyle = IndexLinear())
diagind(M::AbstractMatrix, indstyle::IndexStyle = IndexLinear())
```

행렬 `M`의 `k`번째 대각선의 인덱스를 제공하는 `AbstractRange`입니다. 선택적으로 인덱스 스타일을 지정할 수 있으며, 이는 반환되는 범위의 유형을 결정합니다. `indstyle isa IndexLinear`(기본값)인 경우, 이는 `AbstractRange{Integer}`를 반환합니다. 반면에 `indstyle isa IndexCartesian`인 경우, 이는 `AbstractRange{CartesianIndex{2}}`를 반환합니다.

`k`가 제공되지 않으면 `0`(주 대각선에 해당)으로 간주됩니다.

참고: [`diag`](@ref), [`diagm`](@ref), [`Diagonal`](@ref).

# 예제

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> diagind(A, -1)
2:4:6

julia> diagind(A, IndexCartesian())
StepRangeLen(CartesianIndex(1, 1), CartesianIndex(1, 1), 3)
```

!!! compat "Julia 1.11"
    `IndexStyle`를 지정하려면 최소한 Julia 1.11이 필요합니다.

