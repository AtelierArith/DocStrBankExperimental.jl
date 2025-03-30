```
sprand([rng],[T::Type],m,[n],p::AbstractFloat)
sprand([rng],m,[n],p::AbstractFloat,[rfn=rand])
```

길이가 `m`인 랜덤 희소 벡터 또는 `m` x `n` 희소 행렬을 생성합니다. 이 행렬에서 어떤 요소가 0이 아닐 확률은 독립적으로 `p`로 주어지며 (따라서 비영 값의 평균 밀도도 정확히 `p`입니다). 선택적 `rng` 인자는 난수 생성기를 지정하며, [Random Numbers](@ref)를 참조하십시오. 선택적 `T` 인자는 요소 유형을 지정하며, 기본값은 `Float64`입니다.

기본적으로 비영 값은 [`rand`](@ref) 함수를 사용하여 균일 분포에서 샘플링됩니다. 즉, `rand(T)` 또는 `rng`가 제공된 경우 `rand(rng, T)`로 샘플링됩니다. 기본 `T=Float64`의 경우, 이는 `[0,1)`에서 균일하게 샘플링된 비영 값에 해당합니다.

다른 분포에서 비영 값을 샘플링하려면 `rand` 대신 사용자 정의 `rfn` 함수를 전달하면 됩니다. 이 함수는 원하는 분포에서 샘플링된 `k` 개의 랜덤 숫자의 배열을 반환하는 `rfn(k)`이어야 하며, `rng`가 제공된 경우에는 대신 `rfn(rng, k)`가 되어야 합니다.

# 예제

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> sprand(Bool, 2, 2, 0.5)
2×2 SparseMatrixCSC{Bool, Int64} with 2 stored entries:
 1  1
 ⋅  ⋅

julia> sprand(Float64, 3, 0.75)
3-element SparseVector{Float64, Int64} with 2 stored entries:
  [1]  =  0.795547
  [2]  =  0.49425
```
