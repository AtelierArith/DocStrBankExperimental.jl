```
Perm(order::Ordering, data::AbstractVector)
```

`Ordering` 在 `data` 的索引上，其中如果 `data[i]` 根据 `order` 小于 `data[j]`，则 `i` 小于 `j`。如果 `data[i]` 和 `data[j]` 相等，则通过数值比较 `i` 和 `j`。
