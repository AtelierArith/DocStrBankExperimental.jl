```
issetequal(x)
```

`x`を[`issetequal`](@ref)を使用して比較する関数を作成します。つまり、`y -> issetequal(y, x)`に相当する関数です。返される関数は`Base.Fix2{typeof(issetequal)}`型であり、特化したメソッドを実装するために使用できます。

!!! compat "Julia 1.11"
    この機能は少なくともJulia 1.11が必要です。

