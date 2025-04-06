```
reduce(f, A::AbstractArray; dims=:, [init])
```

2-인수 함수 `f`를 `A`의 차원에 따라 축소합니다. `dims`는 축소할 차원을 지정하는 벡터이며, 키워드 인수 `init`은 축소에 사용할 초기 값입니다. `+`, `*`, `max` 및 `min`의 경우 `init` 인수는 선택 사항입니다.

축소의 결합성은 구현에 따라 다릅니다. 특정 결합성이 필요한 경우, 예를 들어 왼쪽에서 오른쪽으로, 자체 루프를 작성하거나 [`foldl`](@ref) 또는 [`foldr`](@ref) 사용을 고려해야 합니다. [`reduce`](@ref)에 대한 문서를 참조하십시오.

# 예제

```jldoctest
julia> a = reshape(Vector(1:16), (4,4))
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> reduce(max, a, dims=2)
4×1 Matrix{Int64}:
 13
 14
 15
 16

julia> reduce(max, a, dims=1)
1×4 Matrix{Int64}:
 4  8  12  16
```
