```
Eigen <: Factorization
```

정방 행렬 `A`의 고유값/스펙트럼 분해의 행렬 분해 유형입니다. 이는 해당 행렬 분해 함수인 [`eigen`](@ref)의 반환 유형입니다.

`F::Eigen`이 분해 객체인 경우, 고유값은 `F.values`를 통해 얻을 수 있으며, 고유벡터는 행렬 `F.vectors`의 열로 얻을 수 있습니다. (`k`번째 고유벡터는 슬라이스 `F.vectors[:, k]`를 통해 얻을 수 있습니다.)

분해를 반복하면 구성 요소 `F.values`와 `F.vectors`가 생성됩니다.

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
