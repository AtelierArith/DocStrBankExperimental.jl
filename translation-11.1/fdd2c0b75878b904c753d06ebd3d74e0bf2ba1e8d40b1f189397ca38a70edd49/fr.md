```
request(m::AbstractMenu; cursor=1)
```

Affiche le menu et entre en mode interactif. `cursor` indique le numéro de l'élément utilisé pour la position initiale du curseur. `cursor` peut être soit un `Int` soit un `RefValue{Int}`. Ce dernier est utile pour l'observation et le contrôle de la position du curseur de l'extérieur.

Renvoie `selected(m)`.

!!! compat "Julia 1.6"
    L'argument `cursor` nécessite Julia 1.6 ou une version ultérieure.

