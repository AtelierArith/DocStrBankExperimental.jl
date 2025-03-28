```
Base.depwarn(msg::String, funcsym::Symbol; force=false)
```

Imprime `msg` como una advertencia de deprecación. El símbolo `funcsym` debe ser el nombre de la función que llama, que se utiliza para asegurar que la advertencia de deprecación solo se imprima la primera vez para cada lugar de llamada. Establece `force=true` para forzar que la advertencia siempre se muestre, incluso si Julia se inició con `--depwarn=no` (el valor predeterminado).

Ver también [`@deprecate`](@ref).

# Ejemplos

```julia
function deprecated_func()
    Base.depwarn("¡No uses `deprecated_func()`!", :deprecated_func)

    1 + 1
end
```
