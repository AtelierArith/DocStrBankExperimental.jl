```
reinterpret(reshape, T, A::AbstractArray{S}) -> B
```

`A`의 타입 해석을 변경하면서 "채널 차원"을 소비하거나 추가합니다.

`sizeof(T) = n*sizeof(S)`이고 `n>1`인 경우, `A`의 첫 번째 차원은 크기가 `n`이어야 하며 `B`는 `A`의 첫 번째 차원이 없습니다. 반대로, `sizeof(S) = n*sizeof(T)`이고 `n>1`인 경우, `B`는 크기가 `n`인 새로운 첫 번째 차원을 갖습니다. `sizeof(T) == sizeof(S)`인 경우 차원 수는 변경되지 않습니다.

!!! compat "Julia 1.6"
    이 메서드는 최소한 Julia 1.6이 필요합니다.


# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> reinterpret(reshape, Complex{Int}, A)    # 결과는 벡터입니다
2-element reinterpret(reshape, Complex{Int64}, ::Matrix{Int64}) with eltype Complex{Int64}:
 1 + 3im
 2 + 4im

julia> a = [(1,2,3), (4,5,6)]
2-element Vector{Tuple{Int64, Int64, Int64}}:
 (1, 2, 3)
 (4, 5, 6)

julia> reinterpret(reshape, Int, a)             # 결과는 행렬입니다
3×2 reinterpret(reshape, Int64, ::Vector{Tuple{Int64, Int64, Int64}}) with eltype Int64:
 1  4
 2  5
 3  6
```
