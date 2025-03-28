```
print_test_results(ts::AbstractTestSet, depth_pad=0)
```

Imprime los resultados de un `AbstractTestSet` como una tabla formateada.

`depth_pad` se refiere a cuánto relleno se debe agregar frente a toda la salida.

Llamado dentro de `Test.finish`, si el testset `finish`ed es el testset más alto.
