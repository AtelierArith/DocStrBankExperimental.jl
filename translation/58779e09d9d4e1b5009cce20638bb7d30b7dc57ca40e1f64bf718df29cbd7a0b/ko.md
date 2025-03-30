```
in(item, collection) -> Bool
∈(item, collection) -> Bool
```

주어진 컬렉션에 항목이 있는지 확인합니다. 이는 항목이 컬렉션을 반복하여 생성된 값 중 하나와 [`==`](@ref) 같다는 의미입니다. `Bool` 값을 반환하지만, `item`이 [`missing`](@ref) 이거나 `collection`에 `missing`이 포함되어 있지만 `item`은 포함되지 않은 경우에는 `missing`이 반환됩니다 ([삼값 논리](https://en.wikipedia.org/wiki/Three-valued_logic), [`any`](@ref) 및 [`==`](@ref)와 일치하는 동작).

일부 컬렉션은 약간 다른 정의를 따릅니다. 예를 들어, [`Set`](@ref)는 항목이 요소 중 하나와 [`isequal`](@ref) 같은지 확인하고, [`Dict`](@ref)는 `key=>value` 쌍을 찾으며, `key`는 [`isequal`](@ref)로 비교됩니다.

사전에서 키의 존재를 확인하려면 [`haskey`](@ref) 또는 `k in keys(dict)`를 사용하십시오. 위에서 언급한 컬렉션의 경우 결과는 항상 `Bool`입니다.

`in.(items, collection)` 또는 `items .∈ collection`으로 브로드캐스팅할 때, `item`과 `collection` 모두 브로드캐스트되므로 종종 의도한 바가 아닐 수 있습니다. 예를 들어, 두 인수가 벡터이고(차원이 일치하는 경우) 결과는 컬렉션 `items`의 각 값이 `collection`의 해당 위치에 있는 값에 `in`인지 여부를 나타내는 벡터입니다. `items`의 각 값이 `collection`에 있는지 여부를 나타내는 벡터를 얻으려면 `collection`을 튜플이나 `Ref`로 감싸십시오. 예: `in.(items, Ref(collection))` 또는 `items .∈ Ref(collection)`.

또한 참조: [`∉`](@ref), [`insorted`](@ref), [`contains`](@ref), [`occursin`](@ref), [`issubset`](@ref).

# 예제

```jldoctest
julia> a = 1:3:20
1:3:19

julia> 4 in a
true

julia> 5 in a
false

julia> missing in [1, 2]
missing

julia> 1 in [2, missing]
missing

julia> 1 in [1, missing]
true

julia> missing in Set([1, 2])
false

julia> (1=>missing) in Dict(1=>10, 2=>20)
missing

julia> [1, 2] .∈ [2, 3]
2-element BitVector:
 0
 0

julia> [1, 2] .∈ ([2, 3],)
2-element BitVector:
 0
 1
```
