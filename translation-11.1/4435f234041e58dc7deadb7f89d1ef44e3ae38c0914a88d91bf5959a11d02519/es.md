```
base64encode(writefunc, args...; context=nothing)
base64encode(args...; context=nothing)
```

Dada una función similar a [`write`](@ref) llamada `writefunc`, que toma un flujo de I/O como su primer argumento, `base64encode(writefunc, args...)` llama a `writefunc` para escribir `args...` en una cadena codificada en base64 y devuelve la cadena. `base64encode(args...)` es equivalente a `base64encode(write, args...)`: convierte sus argumentos en bytes utilizando las funciones estándar de [`write`](@ref) y devuelve la cadena codificada en base64.

El argumento opcional de palabra clave `context` se puede establecer como un par `:key=>value` o un objeto `IO` o [`IOContext`](@ref) cuyos atributos se utilizan para el flujo de I/O pasado a `writefunc` o `write`.

Véase también [`base64decode`](@ref).
