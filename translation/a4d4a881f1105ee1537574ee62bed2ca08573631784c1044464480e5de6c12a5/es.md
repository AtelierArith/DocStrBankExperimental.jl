```
StackFrame
```

Información de la pila que representa el contexto de ejecución, con los siguientes campos:

  * `func::Symbol`

    El nombre de la función que contiene el contexto de ejecución.
  * `linfo::Union{Core.MethodInstance, Method, Module, Core.CodeInfo, Nothing}`

    La MethodInstance o CodeInfo que contiene el contexto de ejecución (si se pudo encontrar), o Module (para expansiones de macros).
  * `file::Symbol`

    La ruta al archivo que contiene el contexto de ejecución.
  * `line::Int`

    El número de línea en el archivo que contiene el contexto de ejecución.
  * `from_c::Bool`

    Verdadero si el código es de C.
  * `inlined::Bool`

    Verdadero si el código es de un marco en línea.
  * `pointer::UInt64`

    Representación del puntero al contexto de ejecución como lo devuelve `backtrace`.
