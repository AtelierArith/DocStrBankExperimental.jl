```
contains(needle)
```

Crea una función que verifique si su argumento contiene `needle`, es decir, una función equivalente a `haystack -> contains(haystack, needle)`.

La función devuelta es de tipo `Base.Fix2{typeof(contains)}`, que se puede usar para implementar métodos especializados.
