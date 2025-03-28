```
MultiSelectConfig(; charset=:ascii, checked::String, unchecked::String, kwargs...)
```

Configura el comportamiento de un menú de selección múltiple a través de argumentos de palabra clave:

  * `checked` es la cadena que se imprimirá cuando se haya seleccionado una opción. Los valores predeterminados son "[X]" o "✓", dependiendo de `charset`.
  * `unchecked` es la cadena que se imprimirá cuando no se haya seleccionado una opción. Los valores predeterminados son "[ ]" o "⬚", dependiendo de `charset`.

Todos los demás argumentos de palabra clave son como se describe para [`TerminalMenus.Config`](@ref). `checked` y `unchecked` no se imprimen automáticamente y deben ser impresos por tu método `writeline`.

!!! compat "Julia 1.6"
    `MultiSelectConfig` está disponible a partir de Julia 1.6. En versiones anteriores, utiliza el `CONFIG` global.

