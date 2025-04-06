```
isascii(c::Union{AbstractChar,AbstractString}) -> Bool
```

Prueba si un carácter pertenece al conjunto de caracteres ASCII, o si esto es cierto para todos los elementos de una cadena.

# Ejemplos

```jldoctest
julia> isascii('a')
true

julia> isascii('α')
false

julia> isascii("abc")
true

julia> isascii("αβγ")
false
```

Por ejemplo, `isascii` se puede usar como una función predicado para [`filter`](@ref) o [`replace`](@ref) para eliminar o reemplazar caracteres no ASCII, respectivamente:

```jldoctest
julia> filter(isascii, "abcdeγfgh") # descartar caracteres no ASCII
"abcdefgh"

julia> replace("abcdeγfgh", !isascii=>' ') # reemplazar caracteres no ASCII con espacios
"abcde fgh"
```
