```
Test.Error <: Test.Result
```

La condición de prueba no pudo ser evaluada debido a una excepción, o se evaluó a algo diferente de un [`Bool`](@ref). En el caso de `@test_broken`, se utiliza para indicar que ocurrió un `Result` `Pass` inesperado.
