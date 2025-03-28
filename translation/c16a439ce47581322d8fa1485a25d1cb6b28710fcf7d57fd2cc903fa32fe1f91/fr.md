```
display(x)
display(d::AbstractDisplay, x)
display(mime, x)
display(d::AbstractDisplay, mime, x)
```

Affichez `x` en utilisant l'affichage le plus applicable dans la pile d'affichage, généralement en utilisant la sortie multimédia la plus riche prise en charge pour `x`, avec une sortie en texte brut [`stdout`](@ref) comme solution de repli. La variante `display(d, x)` tente d'afficher `x` uniquement sur l'affichage donné `d`, lançant une [`MethodError`](@ref) si `d` ne peut pas afficher des objets de ce type.

En général, vous ne pouvez pas supposer que la sortie de `display` va vers `stdout` (contrairement à [`print(x)`](@ref) ou [`show(x)`](@ref)). Par exemple, `display(x)` peut ouvrir une fenêtre séparée avec une image. `display(x)` signifie "montrez `x` de la meilleure façon possible pour le(s) dispositif(s) de sortie actuel(s)." Si vous souhaitez une sortie textuelle semblable à celle du REPL qui est garantie d'aller vers `stdout`, utilisez [`show(stdout, "text/plain", x)`](@ref) à la place.

Il existe également deux variantes avec un argument `mime` (une chaîne de type MIME, telle que `"image/png"`), qui tentent d'afficher `x` en utilisant le type MIME demandé *uniquement*, lançant une `MethodError` si ce type n'est pas pris en charge par l'affichage ou par `x`. Avec ces variantes, on peut également fournir les données "brutes" dans le type MIME demandé en passant `x::AbstractString` (pour les types MIME avec stockage basé sur du texte, tels que text/html ou application/postscript) ou `x::Vector{UInt8}` (pour les types MIME binaires).

Pour personnaliser la façon dont les instances d'un type sont affichées, surchargez [`show`](@ref) plutôt que `display`, comme expliqué dans la section du manuel sur [l'impression personnalisée](@ref man-custom-pretty-printing).
