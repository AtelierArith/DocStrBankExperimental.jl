```
∉(item, collection) -> Bool
∌(collection, item) -> Bool
```

`∈` と `∋` の否定、すなわち `item` が `collection` に含まれていないことをチェックします。

`items .∉ collection` でブロードキャストすると、`item` と `collection` の両方がブロードキャストされるため、意図した結果にならないことがよくあります。たとえば、両方の引数がベクトルで（次元が一致する場合）、結果は `collection` の対応する位置の値に対して `items` の各値が含まれていないかどうかを示すベクトルになります。`items` の各値が `collection` に含まれていないかどうかを示すベクトルを得るには、`collection` をタプルまたは `Ref` でラップします。例えば、`items .∉ Ref(collection)` のようにします。

# 例

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
