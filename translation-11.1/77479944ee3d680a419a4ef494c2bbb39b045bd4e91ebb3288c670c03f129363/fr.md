```
pushdisplay(d::AbstractDisplay)
```

Pousse un nouvel affichage `d` au sommet de la pile de backend d'affichage global. Appeler `display(x)` ou `display(mime, x)` affichera `x` sur le backend compatible le plus haut dans la pile (c'est-à-dire, le backend le plus haut qui ne génère pas une [`MethodError`](@ref)).
