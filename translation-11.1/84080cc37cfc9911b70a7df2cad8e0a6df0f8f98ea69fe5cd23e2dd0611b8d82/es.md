```
*(s::Union{AbstractString, AbstractChar}, t::Union{AbstractString, AbstractChar}...) -> AbstractString
```

Concatena cadenas y/o caracteres, produciendo un [`String`](@ref) o [`AnnotatedString`](@ref) (según corresponda). Esto es equivalente a llamar a la función [`string`](@ref) o [`annotatedstring`](@ref) sobre los argumentos. La concatenación de tipos de cadena incorporados siempre produce un valor de tipo `String`, pero otros tipos de cadena pueden optar por devolver una cadena de un tipo diferente según corresponda.

# Ejemplos

```jldoctest
julia> "Hello " * "world"
"Hello world"

julia> 'j' * "ulia"
"julia"
```
