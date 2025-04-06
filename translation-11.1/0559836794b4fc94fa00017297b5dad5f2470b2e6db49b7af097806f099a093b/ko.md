```
Bidiagonal(dv::V, ev::V, uplo::Symbol) where V <: AbstractVector
```

주어진 대각선(`dv`) 및 비대각선(`ev`) 벡터를 사용하여 상부(`uplo=:U`) 또는 하부(`uplo=:L`) 이중 대각 행렬을 구성합니다. 결과는 `Bidiagonal` 유형이며 효율적인 특수 선형 솔버를 제공하지만, [`convert(Array, _)`](@ref) (또는 짧게 `Array(_)`)를 사용하여 일반 행렬로 변환할 수 있습니다. `ev`의 길이는 `dv`의 길이보다 하나 적어야 합니다.

# 예제

```jldoctest
julia> dv = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> ev = [7, 8, 9]
3-element Vector{Int64}:
 7
 8
 9

julia> Bu = Bidiagonal(dv, ev, :U) # ev는 첫 번째 초대각선에 있습니다.
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  7  ⋅  ⋅
 ⋅  2  8  ⋅
 ⋅  ⋅  3  9
 ⋅  ⋅  ⋅  4

julia> Bl = Bidiagonal(dv, ev, :L) # ev는 첫 번째 아대각선에 있습니다.
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  ⋅  ⋅  ⋅
 7  2  ⋅  ⋅
 ⋅  8  3  ⋅
 ⋅  ⋅  9  4
```
