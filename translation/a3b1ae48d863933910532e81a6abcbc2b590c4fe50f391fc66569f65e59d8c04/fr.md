```
@doc_str -> MD
```

Analysez la chaîne donnée en tant que texte Markdown, ajoutez des informations de ligne et de module et renvoyez un objet [`MD`](@ref) correspondant.

`@doc_str` peut être utilisé en conjonction avec le module [`Base.Docs`](@ref). Veuillez également vous référer à la section du manuel sur [la documentation](@ref man-documentation) pour plus d'informations.

# Exemples

```
julia> s = doc"f(x) = 2*x"
  f(x) = 2*x

julia> typeof(s)
Markdown.MD

```
