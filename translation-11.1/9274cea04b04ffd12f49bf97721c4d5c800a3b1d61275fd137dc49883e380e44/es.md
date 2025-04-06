```
AnnotatedString{S <: AbstractString} <: AbstractString
```

Una cadena con metadatos, en forma de regiones anotadas.

Más específicamente, este es un simple envoltorio alrededor de cualquier otro [`AbstractString`](@ref) que permite que las regiones de la cadena envuelta sean anotadas con valores etiquetados.

```text
                           C
                    ┌──────┸─────────┐
  "this is an example annotated string"
  └──┰────────┼─────┘         │
     A        └─────┰─────────┘
                    B
```

El diagrama anterior representa un `AnnotatedString` donde tres rangos han sido anotados (etiquetados como `A`, `B` y `C`). Cada anotación contiene una etiqueta (`Symbol`) y un valor (`Any`). Estas tres piezas de información se mantienen como un `@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}`.

Las etiquetas no necesitan ser únicas, la misma región puede contener múltiples anotaciones con la misma etiqueta.

El código escrito para `AnnotatedString`s en general debe conservar las siguientes propiedades:

  * Qué caracteres se aplica una anotación
  * El orden en que se aplican las anotaciones a cada carácter

Semánticas adicionales pueden ser introducidas por usos específicos de `AnnotatedString`s.

Una consecuencia de estas reglas es que anotaciones adyacentes, colocadas consecutivamente, con etiquetas y valores idénticos son equivalentes a una sola anotación que abarca el rango combinado.

Véase también [`AnnotatedChar`](@ref), [`annotatedstring`](@ref), [`annotations`](@ref), y [`annotate!`](@ref).

# Constructores

```julia
AnnotatedString(s::S<:AbstractString) -> AnnotatedString{S}
AnnotatedString(s::S<:AbstractString, annotations::Vector{@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}})
```

Un `AnnotatedString` también se puede crear con [`annotatedstring`](@ref), que actúa de manera similar a [`string`](@ref) pero preserva cualquier anotación presente en los argumentos.

# Ejemplos

```julia-repl
julia> AnnotatedString("this is an example annotated string",
                    [(1:18, :A => 1), (12:28, :B => 2), (18:35, :C => 3)])
"this is an example annotated string"
```
