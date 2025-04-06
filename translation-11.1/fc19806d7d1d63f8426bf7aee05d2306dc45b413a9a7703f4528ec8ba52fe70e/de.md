```
@nif N bedingungsexpr expr
@nif N bedingungsexpr expr sonstexpr
```

Generiert eine Sequenz von `if ... elseif ... else ... end` Anweisungen. Zum Beispiel:

```
@nif 3 d->(i_d >= size(A,d)) d->(error("Dimension ", d, " zu groß")) d->println("Alles OK")
```

würde generieren:

```
if i_1 > size(A, 1)
    error("Dimension ", 1, " zu groß")
elseif i_2 > size(A, 2)
    error("Dimension ", 2, " zu groß")
else
    println("Alles OK")
end
```
