```
RawFD
```

Tipo primitivo que envuelve el descriptor de archivo nativo del sistema operativo. Los `RawFD` se pueden pasar a métodos como [`stat`](@ref) para descubrir información sobre el archivo subyacente, y también se pueden usar para abrir flujos, con el `RawFD` describiendo el archivo del sistema operativo que respalda el flujo.
