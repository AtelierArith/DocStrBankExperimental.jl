```
@nif N conditionexpr expr
@nif N conditionexpr expr elseexpr
```

`if ... elseif ... else ... end` ステートメントのシーケンスを生成します。例えば：

```
@nif 3 d->(i_d >= size(A,d)) d->(error("次元 ", d, " が大きすぎます")) d->println("すべて正常")
```

は次のように生成されます：

```
if i_1 > size(A, 1)
    error("次元 ", 1, " が大きすぎます")
elseif i_2 > size(A, 2)
    error("次元 ", 2, " が大きすぎます")
else
    println("すべて正常")
end
```
