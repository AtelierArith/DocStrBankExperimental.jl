```
*(s::Union{AbstractString, AbstractChar}, t::Union{AbstractString, AbstractChar}...) -> AbstractString
```

Concaténer des chaînes et/ou des caractères, produisant un [`String`](@ref) ou un [`AnnotatedString`](@ref) (selon le cas). Cela équivaut à appeler la fonction [`string`](@ref) ou [`annotatedstring`](@ref) sur les arguments. La concaténation des types de chaînes intégrés produit toujours une valeur de type `String`, mais d'autres types de chaînes peuvent choisir de retourner une chaîne d'un type différent si cela est approprié.

# Exemples

```jldoctest
julia> "Hello " * "world"
"Hello world"

julia> 'j' * "ulia"
"julia"
```
