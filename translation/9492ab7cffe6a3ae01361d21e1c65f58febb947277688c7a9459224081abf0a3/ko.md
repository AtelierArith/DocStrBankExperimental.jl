```
eigen(A, B; sortby) -> GeneralizedEigen
```

`A`와 `B`의 일반화된 고유값 분해를 계산하고, 일반화된 고유값이 `F.values`에, 일반화된 고유벡터가 행렬 `F.vectors`의 열에 포함된 [`GeneralizedEigen`](@ref) 분해 객체 `F`를 반환합니다. 이는 `Ax =  λBx` 형태의 일반화된 고유값 문제를 해결하는 것에 해당하며, 여기서 `A, B`는 행렬, `x`는 고유벡터, `λ`는 고유값입니다. (`k`번째 일반화된 고유벡터는 슬라이스 `F.vectors[:, k]`에서 얻을 수 있습니다.)

분해를 반복하면 구성 요소 `F.values`와 `F.vectors`를 생성합니다.

기본적으로 고유값과 고유벡터는 `(real(λ),imag(λ))`에 따라 사전적으로 정렬됩니다. 다른 비교 함수 `by(λ)`를 `sortby`에 전달하거나, `sortby=nothing`을 전달하여 고유값을 임의의 순서로 남길 수 있습니다.

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

julia> F = eigen(A, B);

julia> F.values
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> F.vectors
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> vals, vecs = F; # 반복을 통한 구조 분해

julia> vals == F.values && vecs == F.vectors
true
```
