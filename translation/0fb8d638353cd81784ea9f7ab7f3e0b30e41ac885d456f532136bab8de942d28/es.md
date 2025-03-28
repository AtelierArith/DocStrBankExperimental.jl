```
@test_deprecated [patrón] expresión
```

Cuando `--depwarn=yes`, prueba que `expresión` emite una advertencia de deprecación y devuelve el valor de `expresión`. La cadena del mensaje de registro se comparará con `patrón`, que por defecto es `r"deprecated"i`.

Cuando `--depwarn=no`, simplemente devuelve el resultado de ejecutar `expresión`. Cuando `--depwarn=error`, verifica que se lance un ErrorException.

# Ejemplos

```
# Deprecado en julia 0.7
@test_deprecated num2hex(1)

# El valor devuelto se puede probar encadenando con @test:
@test (@test_deprecated num2hex(1)) == "0000000000000001"
```
