```
eigen(A; permute::Bool=true, scale::Bool=true, sortby) -> Eigen
```

행렬 `A`의 고유값 분해를 계산하여 고유값이 `F.values`에, 고유벡터가 행렬 `F.vectors`의 열에 포함된 [`Eigen`](@ref) 분해 객체 `F`를 반환합니다. 이는 `Ax =  λx` 형태의 고유값 문제를 해결하는 것에 해당하며, 여기서 `A`는 행렬, `x`는 고유벡터, `λ`는 고유값입니다. (`k`번째 고유벡터는 슬라이스 `F.vectors[:, k]`에서 얻을 수 있습니다.)

분해를 반복하면 구성 요소 `F.values`와 `F.vectors`를 생성합니다.

다음 함수는 `Eigen` 객체에 대해 사용할 수 있습니다: [`inv`](@ref), [`det`](@ref), 및 [`isposdef`](@ref).

일반 비대칭 행렬의 경우 고유벡터 계산 전에 행렬이 어떻게 균형을 이루는지 지정할 수 있습니다. 옵션 `permute=true`는 행렬을 상삼각형에 더 가깝게 만들기 위해 순열을 적용하고, `scale=true`는 행렬의 대각 요소로 행렬을 스케일링하여 행과 열의 노름을 더 평등하게 만듭니다. 기본값은 두 옵션 모두 `true`입니다.

기본적으로 고유값과 고유벡터는 `(real(λ),imag(λ))`에 따라 사전식으로 정렬됩니다. 다른 비교 함수 `by(λ)`를 `sortby`에 전달할 수 있으며, `sortby=nothing`을 전달하여 고유값을 임의의 순서로 남길 수 있습니다. 일부 특수 행렬 유형(예: [`Diagonal`](@ref) 또는 [`SymTridiagonal`](@ref))은 자체 정렬 규칙을 구현할 수 있으며 `sortby` 키워드를 수용하지 않을 수 있습니다.

# 예제

```jldoctest
julia> F = eigen([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
Eigen{Float64, Float64, Matrix{Float64}, Vector{Float64}}
values:
3-element Vector{Float64}:
  1.0
  3.0
 18.0
vectors:
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> F.values
3-element Vector{Float64}:
  1.0
  3.0
 18.0

julia> F.vectors
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> vals, vecs = F; # destructuring via iteration

julia> vals == F.values && vecs == F.vectors
true
```
