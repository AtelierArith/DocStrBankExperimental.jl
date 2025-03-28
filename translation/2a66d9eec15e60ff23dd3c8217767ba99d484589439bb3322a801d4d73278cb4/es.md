```
graphemes(s::AbstractString, m:n) -> SubString
```

Devuelve un [`SubString`](@ref) de `s` que consiste en los grafemas del `m`-ésimo al `n`-ésimo de la cadena `s`, donde el segundo argumento `m:n` es un [`AbstractUnitRange`](@ref) de valores enteros.

Hablando de manera general, esto corresponde a los "caracteres" percibidos por el usuario del `m:n`-ésimo en la cadena. Por ejemplo:

```jldoctest
julia> s = graphemes("exposé", 3:6)
"posé"

julia> collect(s)
5-element Vector{Char}:
 'p': ASCII/Unicode U+0070 (categoría Ll: Letra, minúscula)
 'o': ASCII/Unicode U+006F (categoría Ll: Letra, minúscula)
 's': ASCII/Unicode U+0073 (categoría Ll: Letra, minúscula)
 'e': ASCII/Unicode U+0065 (categoría Ll: Letra, minúscula)
 '́': Unicode U+0301 (categoría Mn: Marca, no espaciadora)
```

Esto consiste en los 3º a *7º* puntos de código ([`Char`](@ref)s) en `"exposé"`, porque el grafema `"é"` es en realidad *dos* puntos de código Unicode (una `'e'` seguida de un carácter combinante de acento agudo U+0301).

Debido a que encontrar los límites de los grafemas requiere iterar sobre el contenido de la cadena, la función `graphemes(s, m:n)` requiere un tiempo proporcional a la longitud de la cadena (número de puntos de código) antes del final de la subcadena.

!!! compat "Julia 1.9"
    El argumento `m:n` de `graphemes` requiere Julia 1.9.

