```
isempty(collection) -> Bool
```

コレクションが空であるか（要素がないか）を判断します。

!!! warning
    `isempty(itr)` は、適切な [`Base.isdone(itr)`](@ref) メソッドが定義されていない限り、状態を持つイテレータ `itr` の次の要素を消費する可能性があります。状態を持つイテレータは *isdone* を実装すべきですが、任意のイテレータタイプをサポートする汎用コードを書く際には `isempty` の使用を避けることをお勧めします。


# 例

```jldoctest
julia> isempty([])
true

julia> isempty([1 2 3])
false
```
