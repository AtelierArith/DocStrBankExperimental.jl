```
@arg_test arg1 arg2 ... cuerpo
```

El macro `@arg_test` se utiliza para convertir las funciones `arg` proporcionadas por `arg_readers` y `arg_writers` en valores de argumento reales. Cuando escribes `@arg_test arg cuerpo`, es equivalente a `arg(arg -> cuerpo)`.
