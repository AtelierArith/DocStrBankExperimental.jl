```
gelqf!(A, tau)
```

行列 `A` の `LQ` 因子分解を計算します。`A = LQ` です。`tau` には因子分解の基本反射をパラメータ化するスカラーが含まれています。`tau` の長さは `A` の最小次元以上でなければなりません。

`A` と `tau` はインプレースで変更されて返されます。
