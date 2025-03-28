```
latex([io::IO], md)
```

Sortie le contenu de l'objet Markdown `md` au format LaTeX, soit en écrivant dans un flux `io` (optionnel), soit en retournant une chaîne.

On peut alternativement utiliser `show(io, "text/latex", md)` ou `repr("text/latex", md)`.

# Exemples

```jldoctest
julia> latex(md"hello _world_")
"hello \\emph{world}\n\n"
```
