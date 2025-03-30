```
GeneralizedEigen <: Factorization
```

`A`와 `B`의 일반화된 고유값/스펙트럼 분해의 행렬 분해 유형입니다. 이는 두 개의 행렬 인수로 호출될 때 해당 행렬 분해 함수인 [`eigen`](@ref)의 반환 유형입니다.

`F::GeneralizedEigen`이 분해 객체인 경우, 고유값은 `F.values`를 통해 얻을 수 있으며, 고유벡터는 행렬 `F.vectors`의 열로 얻을 수 있습니다. (`k`번째 고유벡터는 슬라이스 `F.vectors[:, k]`를 통해 얻을 수 있습니다.)

분해를 반복하면 구성 요소 `F.values`와 `F.vectors`가 생성됩니다.

# 예제

```jldoctest
julia> A = [1 0; 0 -1]
2×2 Matrix{Int64}:
 1   0
 0  -1

julia> B = [0 1; 1 0]
2×2 Matrix{Int64}:
 0  1
 1  0

julia> F = eigen(A, B)
GeneralizedEigen{ComplexF64, ComplexF64, Matrix{ComplexF64}, Vector{ComplexF64}}
values:
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im
vectors:
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> F.values
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> F.vectors
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> vals, vecs = F; # destructuring via iteration

julia> vals == F.values && vecs == F.vectors
true
```
