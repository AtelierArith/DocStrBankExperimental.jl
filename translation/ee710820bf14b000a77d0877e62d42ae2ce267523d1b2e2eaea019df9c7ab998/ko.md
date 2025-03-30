```
Tridiagonal(dl::V, d::V, du::V) where V <: AbstractVector
```

첫 번째 하위 대각선, 대각선 및 첫 번째 상위 대각선으로부터 삼중 대각 행렬을 구성합니다. 결과는 `Tridiagonal` 유형이며 효율적인 특수 선형 솔버를 제공하지만 [`convert(Array, _)`](@ref) (또는 짧게 `Array(_)`)를 사용하여 일반 행렬로 변환할 수 있습니다. `dl` 및 `du`의 길이는 `d`의 길이보다 하나 짧아야 합니다.

!!! note
    하위 대각선 `dl`과 상위 대각선 `du`는 서로 별칭을 가져서는 안 됩니다. 별칭이 감지되면 생성자는 `du`의 복사본을 인수로 사용합니다.


# 예제

```jldoctest
julia> dl = [1, 2, 3];

julia> du = [4, 5, 6];

julia> d = [7, 8, 9, 0];

julia> Tridiagonal(dl, d, du)
4×4 Tridiagonal{Int64, Vector{Int64}}:
 7  4  ⋅  ⋅
 1  8  5  ⋅
 ⋅  2  9  6
 ⋅  ⋅  3  0
```
