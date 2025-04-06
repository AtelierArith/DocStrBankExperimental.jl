```
unescape_string(str::AbstractString, keep = ())::AbstractString
unescape_string(io, s::AbstractString, keep = ())::Nothing
```

Desescapado general de secuencias de escape tradicionales de C y Unicode. La primera forma devuelve la cadena desescapada, la segunda imprime el resultado en `io`. El argumento `keep` especifica una colección de caracteres que (junto con las barras invertidas) se deben mantener tal como están.

Las siguientes secuencias de escape son reconocidas:

  * Barra invertida escapada (`\\`)
  * Comillas dobles escapadas (`\"`)
  * Secuencias de escape estándar de C (`\a`, `\b`, `\t`, `\n`, `\v`, `\f`, `\r`, `\e`)
  * Puntos de código BMP de Unicode (`\u` con 1-4 dígitos hexadecimales finales)
  * Todos los puntos de código de Unicode (`\U` con 1-8 dígitos hexadecimales finales; valor máximo = 0010ffff)
  * Bytes hexadecimales (`\x` con 1-2 dígitos hexadecimales finales)
  * Bytes octales (`\` con 1-3 dígitos octales finales)

Ver también [`escape_string`](@ref).

# Ejemplos

```jldoctest
julia> unescape_string("aaa\\nbbb") # secuencia de escape de C
"aaa\nbbb"

julia> unescape_string("\\u03c0") # unicode
"π"

julia> unescape_string("\\101") # octal
"A"

julia> unescape_string("aaa \\g \\n", ['g']) # usando el argumento `keep`
"aaa \\g \n"
```
