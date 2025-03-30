```
CartesianIndex(i, j, k...)   -> I
CartesianIndex((i, j, k...)) -> I
```

다차원 인덱스 `I`를 생성하여 다차원 배열 `A`의 인덱싱에 사용할 수 있습니다. 특히, `A[I]`는 `A[i,j,k...]`와 동일합니다. 정수와 `CartesianIndex` 인덱스를 자유롭게 혼합할 수 있습니다. 예를 들어, `A[Ipre, i, Ipost]` (여기서 `Ipre`와 `Ipost`는 `CartesianIndex` 인덱스이고 `i`는 `Int`입니다)는 임의의 차원의 배열의 단일 차원에서 작동하는 알고리즘을 작성할 때 유용한 표현이 될 수 있습니다.

`CartesianIndex`는 때때로 [`eachindex`](@ref)에 의해 생성되며, 항상 명시적인 [`CartesianIndices`](@ref)로 반복할 때 생성됩니다.

`I::CartesianIndex`는 `broadcast`에 대해 "스칼라" (컨테이너가 아님)로 처리됩니다. `CartesianIndex`의 구성 요소를 반복하려면 `Tuple(I)`로 변환하십시오.

# 예제

```jldoctest
julia> A = reshape(Vector(1:16), (2, 2, 2, 2))
2×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

[:, :, 2, 1] =
 5  7
 6  8

[:, :, 1, 2] =
  9  11
 10  12

[:, :, 2, 2] =
 13  15
 14  16

julia> A[CartesianIndex((1, 1, 1, 1))]
1

julia> A[CartesianIndex((1, 1, 1, 2))]
9

julia> A[CartesianIndex((1, 1, 2, 1))]
5
```

!!! compat "Julia 1.10"
    `broadcast`에 대한 "스칼라"로서 `CartesianIndex`를 사용하려면 Julia 1.10이 필요합니다. 이전 릴리스에서는 `Ref(I)`를 사용하십시오.

