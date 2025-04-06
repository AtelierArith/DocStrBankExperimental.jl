```
keys(a::AbstractArray)
```

`a`에 대한 모든 유효한 인덱스를 `a` 자체의 형태로 배열로 설명하는 효율적인 배열을 반환합니다.

1차원 배열(벡터)의 키는 정수인 반면, 모든 다른 N차원 배열은 [`CartesianIndex`](@ref)를 사용하여 위치를 설명합니다. 종종 특수 배열 유형인 [`LinearIndices`](@ref)와 [`CartesianIndices`](@ref)는 각각 이러한 정수 배열과 `CartesianIndex`를 효율적으로 표현하는 데 사용됩니다.

배열의 `keys`가 가장 효율적인 인덱스 유형이 아닐 수 있다는 점에 유의하십시오. 최대 성능을 위해서는 대신 [`eachindex`](@ref)를 사용하십시오.

# 예제

```jldoctest
julia> keys([4, 5, 6])
3-element LinearIndices{1, Tuple{Base.OneTo{Int64}}}:
 1
 2
 3

julia> keys([4 5; 6 7])
CartesianIndices((2, 2))
```
