```
AnnotatedChar{S <: AbstractChar} <: AbstractChar
```

Un Char avec des annotations.

Plus précisément, il s'agit d'un simple wrapper autour de tout autre [`AbstractChar`](@ref), qui contient une liste d'annotations étiquetées arbitraires (`@NamedTuple{label::Symbol, value}`) avec le caractère encapsulé.

Voir aussi : [`AnnotatedString`](@ref), [`annotatedstring`](@ref), `annotations`, et `annotate!`.

# Constructeurs

```julia
AnnotatedChar(s::S) -> AnnotatedChar{S}
AnnotatedChar(s::S, annotations::Vector{@NamedTuple{label::Symbol, value}})
```

# Exemples

```julia-repl
julia> AnnotatedChar('j', :label => 1)
'j': ASCII/Unicode U+006A (catégorie Ll: Lettre, minuscule)
```
