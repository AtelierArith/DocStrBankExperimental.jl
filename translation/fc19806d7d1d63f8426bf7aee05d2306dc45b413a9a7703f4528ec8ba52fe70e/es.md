```
@nif N conditionexpr expr
@nif N conditionexpr expr elseexpr
```

Genera una secuencia de declaraciones `if ... elseif ... else ... end`. Por ejemplo:

```
@nif 3 d->(i_d >= size(A,d)) d->(error("Dimensión ", d, " demasiado grande")) d->println("Todo OK")
```

generaría:

```
if i_1 > size(A, 1)
    error("Dimensión ", 1, " demasiado grande")
elseif i_2 > size(A, 2)
    error("Dimensión ", 2, " demasiado grande")
else
    println("Todo OK")
end
```
