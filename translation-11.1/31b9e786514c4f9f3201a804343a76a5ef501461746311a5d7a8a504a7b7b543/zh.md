```
@nall N expr
```

检查由匿名函数表达式 `expr` 生成的所有表达式是否都评估为 `true`。

`@nall 3 d->(i_d > 1)` 将生成表达式 `(i_1 > 1 && i_2 > 1 && i_3 > 1)`。这对于边界检查非常方便。
