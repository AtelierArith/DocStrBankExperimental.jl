```
∉(item, collection) -> Bool
∌(collection, item) -> Bool
```

`∈`와 `∋`의 부정, 즉 `item`이 `collection`에 없음을 확인합니다.

`items .∉ collection`으로 브로드캐스팅할 때, `item`과 `collection` 모두 브로드캐스트되므로, 이는 종종 의도한 바가 아닙니다. 예를 들어, 두 인수가 벡터이고(차원이 일치하는 경우) 결과는 `collection`의 해당 위치에 있는 값이 아닌 `items`의 각 값이 아닌지를 나타내는 벡터입니다. `items`의 각 값이 `collection`에 없음을 나타내는 벡터를 얻으려면, `collection`을 튜플이나 `Ref`로 감싸야 합니다. 예: `items .∉ Ref(collection)`.

# 예제

```jldoctest
julia> 1 ∉ 2:4
true

julia> 1 ∉ 1:3
false

julia> [1, 2] .∉ [2, 3]
2-element BitVector:
 1
 1

julia> [1, 2] .∉ ([2, 3],)
2-element BitVector:
 1
 0
```
