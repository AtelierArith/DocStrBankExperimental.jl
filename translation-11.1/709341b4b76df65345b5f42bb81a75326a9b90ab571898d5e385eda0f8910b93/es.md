```
Fix1(f, x)
```

Un tipo que representa una versión parcialmente aplicada de la función de dos argumentos `f`, con el primer argumento fijado al valor "x". En otras palabras, `Fix1(f, x)` se comporta de manera similar a `y->f(x, y)`.

Véase también [`Fix2`](@ref Base.Fix2).
