```
reshape(A, dims...) -> AbstractArray
reshape(A, dims) -> AbstractArray
```

`A`와 동일한 데이터를 가진 배열을 반환하지만, 차원 크기나 차원 수가 다릅니다. 두 배열은 동일한 기본 데이터를 공유하므로, 결과는 `A`가 변경 가능할 때만 변경 가능하며, 하나의 요소를 설정하면 다른 요소의 값이 변경됩니다.

새로운 차원은 인수 목록 또는 형태 튜플로 지정할 수 있습니다. 최대 하나의 차원만 `:`로 지정할 수 있으며, 이 경우 그 길이는 지정된 모든 차원과의 곱이 원래 배열 `A`의 길이와 같도록 계산됩니다. 총 요소 수는 변경될 수 없습니다.

# 예제

```jldoctest
julia> A = Vector(1:16)
16-element Vector{Int64}:
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16

julia> reshape(A, (4, 4))
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> reshape(A, 2, :)
2×8 Matrix{Int64}:
 1  3  5  7   9  11  13  15
 2  4  6  8  10  12  14  16

julia> reshape(1:6, 2, 3)
2×3 reshape(::UnitRange{Int64}, 2, 3) with eltype Int64:
 1  3  5
 2  4  6
```
