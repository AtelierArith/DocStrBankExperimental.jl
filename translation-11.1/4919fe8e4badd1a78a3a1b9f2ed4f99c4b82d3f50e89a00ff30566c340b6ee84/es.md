```
stringmime(mime, x; context=nothing)
```

Devuelve un `AbstractString` que contiene la representación de `x` en el tipo `mime` solicitado. Esto es similar a [`repr(mime, x)`](@ref) excepto que los datos binarios se codifican en base64 como una cadena ASCII.

El argumento de palabra clave opcional `context` se puede establecer en un par `:key=>value` o un objeto `IO` o [`IOContext`](@ref) cuyos atributos se utilizan para el flujo de I/O pasado a [`show`](@ref).
