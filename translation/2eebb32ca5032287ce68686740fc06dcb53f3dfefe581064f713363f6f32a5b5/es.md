```
lookup(pointer::Ptr{Cvoid}) -> Vector{StackFrame}
```

Dado un puntero a un contexto de ejecución (generalmente generado por una llamada a `backtrace`), busca información del contexto del marco de pila. Devuelve un arreglo de información del marco para todas las funciones en línea en ese punto, comenzando por la función más interna.
