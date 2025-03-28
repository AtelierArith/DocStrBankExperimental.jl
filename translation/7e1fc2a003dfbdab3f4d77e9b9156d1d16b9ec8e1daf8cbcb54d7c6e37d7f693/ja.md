```
givens(f::T, g::T, i1::Integer, i2::Integer) where {T} -> (G::Givens, r::T)
```

Givens回転`G`とスカラー`r`を計算します。これは任意のベクトル`x`に対して

```
x[i1] = f
x[i2] = g
```

のとき、乗算の結果が

```
y = G*x
```

以下の性質を持つことを意味します。

```
y[i1] = r
y[i2] = 0
```

詳細は[`LinearAlgebra.Givens`](@ref)を参照してください。
