```
reverse(s::AbstractString) -> AbstractString
```

Revierte una cadena. Técnicamente, esta función revierte los puntos de código en una cadena y su principal utilidad es para el procesamiento de cadenas en orden inverso, especialmente para búsquedas de expresiones regulares en orden inverso. Véase también [`reverseind`](@ref) para convertir índices en `s` a índices en `reverse(s)` y viceversa, y `graphemes` del módulo `Unicode` para operar en "caracteres" visibles para el usuario (grafemas) en lugar de puntos de código. Véase también [`Iterators.reverse`](@ref) para iteración en orden inverso sin hacer una copia. Los tipos de cadena personalizados deben implementar la función `reverse` ellos mismos y típicamente deben devolver una cadena con el mismo tipo y codificación. Si devuelven una cadena con una codificación diferente, también deben anular `reverseind` para ese tipo de cadena para satisfacer `s[reverseind(s,i)] == reverse(s)[i]`.

# Ejemplos

```jldoctest
julia> reverse("JuliaLang")
"gnaLailuJ"
```

!!! nota
    Los ejemplos a continuación pueden renderizarse de manera diferente en diferentes sistemas. Los comentarios indican cómo se supone que deben renderizarse.


Los caracteres combinados pueden llevar a resultados sorprendentes:

```jldoctest
julia> reverse("ax̂e") # el sombrero está sobre la x en la entrada, sobre la e en la salida
"êxa"

julia> using Unicode

julia> join(reverse(collect(graphemes("ax̂e")))) # revierte grafemas; el sombrero está sobre la x en ambas entradas y salidas
"ex̂a"
```
