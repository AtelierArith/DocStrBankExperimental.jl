```
grad(f, args...; seed=1)
```

呼び出し可能な `f` の引数に関する勾配を求めます。

`grad()` は二つのものを返します：`f(args...)` の値と、その入力（呼び出し可能なもの自体を含む）に関する勾配のタプルです。

```jldoctest
using Yota   # hide

val, g = grad(x -> sum(x .+ 1), [1.0, 2.0, 3.0])

# output
(9.0, (ChainRulesCore.ZeroTangent(), [1.0, 1.0, 1.0]))
```

デフォルトでは、`grad()` は呼び出し可能なものがスカラーを返すことを期待します。ベクトル値関数は、シード（開始値）が提供されると微分可能です。シードはVJP表記におけるベクトルに相当します。

```jldoctest
using Yota   # hide

val, g = grad(x -> 2x, [1.0, 2.0, 3.0]; seed=ones(3))

# output
([2.0, 4.0, 6.0], (ChainRulesCore.ZeroTangent(), [2.0, 2.0, 2.0]))
```

すべての勾配は、`update!()` 関数を使用して元の変数に適用できます。

関連情報: [gradtape](@ref)
