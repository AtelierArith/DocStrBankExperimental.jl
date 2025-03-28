```
writeline(buf::IO, m::AbstractMenu, idx::Int, iscursor::Bool)
```

Escribe la opción en el índice `idx` en `buf`. `iscursor`, si es `true`, indica que este elemento está en la posición actual del cursor (la que se seleccionará al presionar "Enter").

Si `m` es un `ConfiguredMenu`, `TerminalMenus` imprimirá el indicador del cursor. De lo contrario, se espera que el llamador maneje dicha impresión.

!!! compat "Julia 1.6"
    `writeline` requiere Julia 1.6 o superior.

    En versiones anteriores de Julia, esto era `writeLine(buf::IO, m::AbstractMenu, idx, iscursor::Bool)` y se asume que `m` no está configurado. Los indicadores de selección y cursor se pueden obtener de `TerminalMenus.CONFIG`.

    Esta función más antigua es compatible con todas las versiones de Julia 1.x, pero se eliminará en Julia 2.0.

