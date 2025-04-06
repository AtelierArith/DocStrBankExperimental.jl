```
redisplay(x)
redisplay(d::AbstractDisplay, x)
redisplay(mime, x)
redisplay(d::AbstractDisplay, mime, x)
```

Par défaut, les fonctions `redisplay` appellent simplement [`display`](@ref). Cependant, certains backends d'affichage peuvent remplacer `redisplay` pour modifier un affichage existant de `x` (le cas échéant). Utiliser `redisplay` est également un indice pour le backend que `x` peut être réaffiché plusieurs fois, et le backend peut choisir de différer l'affichage jusqu'à (par exemple) la prochaine invite interactive.
