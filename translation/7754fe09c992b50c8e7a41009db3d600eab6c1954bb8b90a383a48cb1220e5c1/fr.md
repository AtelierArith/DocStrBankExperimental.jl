```
@md_str -> MD
```

Analysez la chaîne donnée en tant que texte Markdown et renvoyez un objet correspondant [`MD`](@ref).

# Exemples

```jldoctest
julia> s = md"# Bonjour, le monde!"
  Bonjour, le monde!
  ≡≡≡≡≡≡≡≡≡≡≡≡≡

julia> typeof(s)
Markdown.MD

```
