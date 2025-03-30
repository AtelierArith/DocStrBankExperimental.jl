```
pushfirst!(collection, items...) -> collection
```

在 `collection` 的开头插入一个或多个 `items`。

在许多其他编程语言中，这个函数被称为 `unshift`。

# 示例

```jldoctest
julia> pushfirst!([1, 2, 3, 4], 5, 6)
6-element Vector{Int64}:
 5
 6
 1
 2
 3
 4
```
