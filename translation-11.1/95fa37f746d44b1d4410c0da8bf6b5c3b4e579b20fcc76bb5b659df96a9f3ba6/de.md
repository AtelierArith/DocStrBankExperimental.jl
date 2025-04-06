```
AnnotatedChar{S <: AbstractChar} <: AbstractChar
```

Ein Char mit Anmerkungen.

Genauer gesagt, ist dies ein einfacher Wrapper um jeden anderen [`AbstractChar`](@ref), der eine Liste von beliebigen beschrifteten Anmerkungen (`@NamedTuple{label::Symbol, value}`) mit dem umschlossenen Zeichen hält.

Siehe auch: [`AnnotatedString`](@ref), [`annotatedstring`](@ref), `annotations` und `annotate!`.

# Konstruktoren

```julia
AnnotatedChar(s::S) -> AnnotatedChar{S}
AnnotatedChar(s::S, annotations::Vector{@NamedTuple{label::Symbol, value}})
```

# Beispiele

```julia-repl
julia> AnnotatedChar('j', :label => 1)
'j': ASCII/Unicode U+006A (Kategorie Ll: Buchstabe, Kleinbuchstabe)
```
