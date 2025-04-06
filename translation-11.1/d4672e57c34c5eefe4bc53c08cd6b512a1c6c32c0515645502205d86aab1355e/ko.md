```
eigvals!(A; permute::Bool=true, scale::Bool=true, sortby) -> values
```

[`eigvals`](@ref)와 동일하지만, 입력 `A`를 덮어써서 공간을 절약합니다. `permute`, `scale`, 및 `sortby` 키워드는 [`eigen`](@ref)와 동일합니다.

!!! note
    `eigvals!`가 호출된 후 입력 행렬 `A`는 고유값을 포함하지 않습니다 - `A`는 작업 공간으로 사용됩니다.


# 예제

```jldoctest
julia> A = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> eigvals!(A)
2-element Vector{Float64}:
 -0.3722813232690143
  5.372281323269014

julia> A
2×2 Matrix{Float64}:
 -0.372281  -1.0
  0.0        5.37228
```
