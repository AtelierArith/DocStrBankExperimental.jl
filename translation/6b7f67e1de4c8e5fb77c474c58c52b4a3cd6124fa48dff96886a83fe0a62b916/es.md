```
TestCounts
```

Mantiene el estado para recopilar recursivamente los resultados de un conjunto de pruebas con fines de visualización.

Campos:

  * `customized`: Si la función `get_test_counts` fue personalizada para el `AbstractTestSet` para el cual este objeto de conteo es. Si se definió un método personalizado, siempre pase `true` al constructor.
  * `passes`: El número de invocaciones `@test` que pasaron.
  * `fails`: El número de invocaciones `@test` que fallaron.
  * `errors`: El número de invocaciones `@test` que tuvieron errores.
  * `broken`: El número de invocaciones `@test` que están rotas.
  * `passes`: El número acumulativo de invocaciones `@test` que pasaron.
  * `fails`: El número acumulativo de invocaciones `@test` que fallaron.
  * `errors`: El número acumulativo de invocaciones `@test` que tuvieron errores.
  * `broken`: El número acumulativo de invocaciones `@test` que están rotas.
  * `duration`: La duración total durante la cual el `AbstractTestSet` en cuestión se ejecutó, como una `String` formateada.
