```
stacktrace([trace::Vector{Ptr{Cvoid}},] [c_funcs::Bool=false]) -> StackTrace
```

Devuelve un rastreo de pila en forma de un vector de `StackFrame`s. (Por defecto, stacktrace no devuelve funciones C, pero esto se puede habilitar). Cuando se llama sin especificar un rastreo, `stacktrace` primero llama a `backtrace`.
