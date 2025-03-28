```
show([io::IO = stdout], x)
```

Escribe una representación de texto de un valor `x` en el flujo de salida `io`. Los nuevos tipos `T` deben sobrecargar `show(io::IO, x::T)`. La representación utilizada por `show` generalmente incluye formato específico de Julia e información de tipo, y debe ser código Julia que se pueda analizar cuando sea posible.

[`repr`](@ref) devuelve la salida de `show` como una cadena.

Para una salida de texto más detallada y legible para humanos para objetos del tipo `T`, define `show(io::IO, ::MIME"text/plain", ::T)` además. Se recomienda verificar la clave `:compact` del [`IOContext`](@ref) (a menudo verificada como `get(io, :compact, false)::Bool`) de `io` en tales métodos, ya que algunos contenedores muestran sus elementos llamando a este método con `:compact => true`.

Consulta también [`print`](@ref), que escribe representaciones no decoradas.

# Ejemplos

```jldoctest
julia> show("Hello World!")
"Hello World!"
julia> print("Hello World!")
Hello World!
```
