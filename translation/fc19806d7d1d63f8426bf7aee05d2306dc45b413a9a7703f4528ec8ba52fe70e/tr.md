```
@nif N conditionexpr expr
@nif N conditionexpr expr elseexpr
```

`if ... elseif ... else ... end` ifadelerinin bir dizisini oluşturur. Örneğin:

```
@nif 3 d->(i_d >= size(A,d)) d->(error("Boyut ", d, " çok büyük")) d->println("Her şey tamam")
```

şu şekilde oluşturulacaktır:

```
if i_1 > size(A, 1)
    error("Boyut ", 1, " çok büyük")
elseif i_2 > size(A, 2)
    error("Boyut ", 2, " çok büyük")
else
    println("Her şey tamam")
end
```
