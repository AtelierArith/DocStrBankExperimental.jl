```
printstyled([io], xs...; bold::Bool=false, italic::Bool=false, underline::Bool=false, blink::Bool=false, reverse::Bool=false, hidden::Bool=false, color::Union{Symbol,Int}=:normal)
```

Imprime `xs` dans une couleur spécifiée comme un symbole ou un entier, éventuellement en gras.

Le mot-clé `color` peut prendre n'importe quelle des valeurs `:normal`, `:italic`, `:default`, `:bold`, `:black`, `:blink`, `:blue`, `:cyan`, `:green`, `:hidden`, `:light_black`, `:light_blue`, `:light_cyan`, `:light_green`, `:light_magenta`, `:light_red`, `:light_white`, `:light_yellow`, `:magenta`, `:nothing`, `:red`, `:reverse`, `:underline`, `:white`, ou `:yellow` ou un entier entre 0 et 255 inclus. Notez que tous les terminaux ne prennent pas en charge 256 couleurs.

Les mots-clés `bold=true`, `italic=true`, `underline=true`, `blink=true` sont explicites. Le mot-clé `reverse=true` imprime avec les couleurs de premier plan et d'arrière-plan échangées, et `hidden=true` devrait être invisible dans le terminal mais peut toujours être copié. Ces propriétés peuvent être utilisées dans n'importe quelle combinaison.

Voir aussi [`print`](@ref), [`println`](@ref), [`show`](@ref).

!!! note
    Tous les terminaux ne prennent pas en charge la sortie en italique. Certains terminaux interprètent l'italique comme un inverse ou un clignotement.


!!! compat "Julia 1.7"
    Les mots-clés sauf `color` et `bold` ont été ajoutés dans Julia 1.7.


!!! compat "Julia 1.10"
    Le support pour la sortie en italique a été ajouté dans Julia 1.10.

