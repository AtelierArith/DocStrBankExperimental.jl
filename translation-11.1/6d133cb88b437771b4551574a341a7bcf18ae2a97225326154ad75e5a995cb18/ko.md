```
sprandn([rng][,Type],m[,n],p::AbstractFloat)
```

길이가 `m`인 임의의 희소 벡터 또는 크기가 `m` x `n`인 희소 행렬을 생성하며, 각 항목이 0이 아닐 확률 `p`를 지정합니다. 0이 아닌 값은 정규 분포에서 샘플링됩니다. 선택적 `rng` 인자는 난수 생성기를 지정하며, [난수](@ref)를 참조하십시오.

!!! compat "Julia 1.1"
    출력 요소 유형 `Type`을 지정하려면 최소한 Julia 1.1이 필요합니다.


# 예제

```jldoctest; setup = :(using Random; Random.seed!(0))
julia> sprandn(2, 2, 0.75)
2×2 SparseMatrixCSC{Float64, Int64} with 3 stored entries:
 -1.20577     ⋅
  0.311817  -0.234641
```
