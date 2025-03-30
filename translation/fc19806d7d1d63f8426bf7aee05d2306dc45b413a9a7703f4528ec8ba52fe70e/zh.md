```
@nif N conditionexpr expr
@nif N conditionexpr expr elseexpr
```

生成一系列 `if ... elseif ... else ... end` 语句。例如：

```
@nif 3 d->(i_d >= size(A,d)) d->(error("Dimension ", d, " too big")) d->println("All OK")
```

将生成：

```
if i_1 > size(A, 1)
    error("Dimension ", 1, " too big")
elseif i_2 > size(A, 2)
    error("Dimension ", 2, " too big")
else
    println("All OK")
end
```
