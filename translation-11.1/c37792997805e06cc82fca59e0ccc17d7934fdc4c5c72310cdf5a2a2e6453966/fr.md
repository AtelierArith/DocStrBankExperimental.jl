```
html([io::IO], md)
```

Affiche le contenu de l'objet Markdown `md` au format HTML, soit en écrivant dans un flux `io` (optionnel), soit en retournant une chaîne.

On peut également utiliser `show(io, "text/html", md)` ou `repr("text/html", md)`, qui diffèrent en ce sens qu'ils enveloppent la sortie dans un élément `<div class="markdown"> ... </div>`.

# Exemples

```jldoctest
julia> html(md"hello _world_")
"<p>hello <em>world</em></p>\n"
```
