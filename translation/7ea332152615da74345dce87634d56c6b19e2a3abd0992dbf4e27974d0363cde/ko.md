```
eigvals!(A, B; sortby) -> values
```

[`eigvals`](@ref)와 동일하지만, 복사본을 생성하는 대신 입력 `A`(및 `B`)를 덮어써서 공간을 절약합니다.

!!! note
    `eigvals!`가 호출된 후 입력 행렬 `A`와 `B`는 고유값을 포함하지 않습니다. 이들은 작업 공간으로 사용됩니다.


# 예제

```jldoctest
julia> A = [1. 0.; 0. -1.]
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> B = [0. 1.; 1. 0.]
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> eigvals!(A, B)
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> A
2×2 Matrix{Float64}:
 -0.0  -1.0
  1.0  -0.0

julia> B
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
