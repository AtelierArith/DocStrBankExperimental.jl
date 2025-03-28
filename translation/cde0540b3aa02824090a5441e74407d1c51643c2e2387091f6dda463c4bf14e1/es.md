```
remove_frames!(stack::StackTrace, name::Symbol)
```

Toma un `StackTrace` (un vector de `StackFrames`) y un nombre de función (un `Symbol`) y elimina el `StackFrame` especificado por el nombre de la función del `StackTrace` (eliminando también todos los frames por encima de la función especificada). Se utiliza principalmente para eliminar funciones de `StackTraces` del `StackTrace` antes de devolverlo.
