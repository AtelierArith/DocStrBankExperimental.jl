```
geqlf!(A) -> (A, tau)
```

行列 `A` の `QL` 因子分解を計算します。すなわち、`A = QL` です。

インプレースで変更された `A` と、因子分解の基本反射をパラメータ化するスカラーを含む `tau` を返します。
