```
LinearIndices(A::AbstractArray)
```

`A`와 동일한 형태와 [`axes`](@ref)를 가진 `LinearIndices` 배열을 반환하며, `A`의 각 항목에 대한 선형 인덱스를 보유합니다. 이 배열을 카르테시안 인덱스로 인덱싱하면 선형 인덱스에 매핑할 수 있습니다.

전통적인 인덱싱(인덱스가 1에서 시작) 또는 다차원 배열의 경우, 선형 인덱스는 1에서 `length(A)`까지 범위입니다. 그러나 `AbstractVector`의 경우 선형 인덱스는 `axes(A, 1)`이며, 따라서 비전통적인 인덱싱을 가진 벡터의 경우 1에서 시작하지 않습니다.

이 함수를 호출하는 것은 선형 인덱싱을 활용하는 알고리즘을 작성하는 "안전한" 방법입니다.

# 예제

```jldoctest
julia> A = fill(1, (5,6,7));

julia> b = LinearIndices(A);

julia> extrema(b)
(1, 210)
```

```
LinearIndices(inds::CartesianIndices) -> R
LinearIndices(sz::Dims) -> R
LinearIndices((istart:istop, jstart:jstop, ...)) -> R
```

지정된 형태 또는 [`axes`](@ref)를 가진 `LinearIndices` 배열을 반환합니다.

# 예제

이 생성자의 주요 목적은 카르테시안 인덱싱에서 선형 인덱싱으로의 직관적인 변환입니다:

```jldoctest
julia> linear = LinearIndices((1:3, 1:2))
3×2 LinearIndices{2, Tuple{UnitRange{Int64}, UnitRange{Int64}}}:
 1  4
 2  5
 3  6

julia> linear[1,2]
4
```
