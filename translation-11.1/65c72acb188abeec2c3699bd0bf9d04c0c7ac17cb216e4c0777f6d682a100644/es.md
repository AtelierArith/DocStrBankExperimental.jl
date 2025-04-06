"     get*test*counts(::AbstractTestSet) -> TestCounts

Función recursiva que cuenta el número de resultados de prueba de cada tipo directamente en el conjunto de pruebas, y totaliza a través de los conjuntos de pruebas hijos.

Los `AbstractTestSet` personalizados deben implementar esta función para que sus totales sean contados y mostrados con `DefaultTestSet` también.

Si esto no se implementa para un `TestSet` personalizado, la impresión vuelve a reportar `x` para fallos y `?s` para la duración.
