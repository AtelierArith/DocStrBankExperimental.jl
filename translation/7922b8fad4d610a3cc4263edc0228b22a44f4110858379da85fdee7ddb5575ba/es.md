```
titlecase(s::AbstractString; [wordsep::Function], strict::Bool=true) -> String
```

Capitaliza el primer carácter de cada palabra en `s`; si `strict` es verdadero, cada otro carácter se convierte en minúscula, de lo contrario se dejan sin cambios. Por defecto, todos los no-letras que comienzan un nuevo grafema se consideran como separadores de palabras; se puede pasar un predicado como el argumento `wordsep` para determinar qué caracteres deben considerarse como separadores de palabras. Ver también [`uppercasefirst`](@ref) para capitalizar solo el primer carácter en `s`.

Ver también [`uppercase`](@ref), [`lowercase`](@ref), [`uppercasefirst`](@ref).

# Ejemplos

```jldoctest
julia> titlecase("the JULIA programming language")
"The Julia Programming Language"

julia> titlecase("ISS - international space station", strict=false)
"ISS - International Space Station"

julia> titlecase("a-a b-b", wordsep = c->c==' ')
"A-a B-b"
```
