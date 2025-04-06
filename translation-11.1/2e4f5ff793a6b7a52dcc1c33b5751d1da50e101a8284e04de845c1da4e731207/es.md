```
edit(function, [types])
edit(module)
```

Edita la definición de una función, especificando opcionalmente una tupla de tipos para indicar qué método editar. Para los módulos, abre el archivo fuente principal. El módulo debe ser cargado con `using` o `import` primero.

!!! compat "Julia 1.1"
    `edit` en módulos requiere al menos Julia 1.1.


Para asegurarte de que el archivo se pueda abrir en la línea dada, es posible que necesites llamar a `InteractiveUtils.define_editor` primero.
