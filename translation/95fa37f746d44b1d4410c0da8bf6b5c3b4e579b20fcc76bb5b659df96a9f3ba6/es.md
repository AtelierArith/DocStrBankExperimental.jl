```
AnnotatedChar{S <: AbstractChar} <: AbstractChar
```

Un Char con anotaciones.

Más específicamente, este es un simple envoltorio alrededor de cualquier otro [`AbstractChar`](@ref), que contiene una lista de anotaciones etiquetadas arbitrarias (`@NamedTuple{label::Symbol, value}`) con el carácter envuelto.

Véase también: [`AnnotatedString`](@ref), [`annotatedstring`](@ref), `annotations`, y `annotate!`.

# Constructores

```julia
AnnotatedChar(s::S) -> AnnotatedChar{S}
AnnotatedChar(s::S, annotations::Vector{@NamedTuple{label::Symbol, value}})
```

# Ejemplos

```julia-repl
julia> AnnotatedChar('j', :label => 1)
'j': ASCII/Unicode U+006A (categoría Ll: Letra, minúscula)
```
