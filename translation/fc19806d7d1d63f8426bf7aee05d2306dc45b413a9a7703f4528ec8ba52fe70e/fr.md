```
@nif N conditionexpr expr
@nif N conditionexpr expr elseexpr
```

Génère une séquence d'instructions `if ... elseif ... else ... end`. Par exemple :

```
@nif 3 d->(i_d >= size(A,d)) d->(error("Dimension ", d, " trop grande")) d->println("Tout va bien")
```

générerait :

```
if i_1 > size(A, 1)
    error("Dimension ", 1, " trop grande")
elseif i_2 > size(A, 2)
    error("Dimension ", 2, " trop grande")
else
    println("Tout va bien")
end
```
