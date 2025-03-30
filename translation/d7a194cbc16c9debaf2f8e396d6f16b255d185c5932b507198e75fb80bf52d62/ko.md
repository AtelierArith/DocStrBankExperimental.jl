```
collect(collection)
```

컬렉션 또는 반복자의 모든 항목을 포함하는 `Array`를 반환합니다. 사전의 경우 `key=>value` [Pair](@ref Pair)로 이루어진 `Vector`를 반환합니다. 인수가 배열과 유사하거나 [`HasShape`](@ref IteratorSize) 특성을 가진 반복자인 경우, 결과는 인수와 동일한 형태와 차원 수를 가집니다.

[comprehensions](@ref man-comprehensions)에서 [generator expression](@ref man-generators)을 `Array`로 변환하는 데 사용됩니다. 따라서 *제너레이터에서*는 `collect`를 호출하는 대신 대괄호 표기법을 사용할 수 있습니다. 두 번째 예를 참조하세요.

# 예제

`UnitRange{Int64}` 컬렉션에서 항목 수집:

```jldoctest
julia> collect(1:3)
3-element Vector{Int64}:
 1
 2
 3
```

제너레이터에서 항목 수집 (출력은 `[x^2 for x in 1:3]`와 동일):

```jldoctest
julia> collect(x^2 for x in 1:3)
3-element Vector{Int64}:
 1
 4
 9
```
