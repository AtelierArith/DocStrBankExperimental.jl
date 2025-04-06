```
IOContext
```

`IOContext` proporciona un mecanismo para pasar configuraciones de salida entre los métodos [`show`](@ref).

En resumen, es un diccionario inmutable que es una subclase de `IO`. Soporta operaciones estándar de diccionario como [`getindex`](@ref), y también puede ser utilizado como un flujo de I/O.
