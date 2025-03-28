```
isequal(x)
```

引数を `x` と比較する関数を作成します。これは [`isequal`](@ref) を使用するもので、すなわち `y -> isequal(y, x)` に相当する関数です。

返される関数は `Base.Fix2{typeof(isequal)}` 型であり、特化したメソッドを実装するために使用できます。
