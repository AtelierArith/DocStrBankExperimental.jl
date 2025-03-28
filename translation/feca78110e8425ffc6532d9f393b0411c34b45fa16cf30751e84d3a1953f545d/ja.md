```
Perm(order::Ordering, data::AbstractVector)
```

`Ordering`は`data`のインデックスに対して、`data[i]`が`data[j]`より小さい場合に`i`が`j`より小さいとします。`data[i]`と`data[j]`が等しい場合は、`i`と`j`は数値で比較されます。
