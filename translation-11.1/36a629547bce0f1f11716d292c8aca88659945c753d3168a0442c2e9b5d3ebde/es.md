```
print([io::IO], xs...)
```

Escribe en `io` (o en el flujo de salida predeterminado [`stdout`](@ref) si `io` no se proporciona) una representación de texto canónica (sin decoración). La representación utilizada por `print` incluye un formato mínimo y trata de evitar detalles específicos de Julia.

`print` recurre a llamar a `show`, por lo que la mayoría de los tipos solo deberían definir `show`. Define `print` si tu tipo tiene una representación "plana" separada. Por ejemplo, `show` muestra cadenas con comillas, y `print` muestra cadenas sin comillas.

Consulta también [`println`](@ref), [`string`](@ref), [`printstyled`](@ref).

# Ejemplos

```jldoctest
julia> print("¡Hola Mundo!")
¡Hola Mundo!
julia> io = IOBuffer();

julia> print(io, "Hola", ' ', :Mundo!)

julia> String(take!(io))
"Hola Mundo!"
```
