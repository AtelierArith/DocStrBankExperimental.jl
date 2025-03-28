```
setrounding(f::Function, T, mode)
```

Changez le mode d'arrondi du type de point flottant `T` pour la durée de `f`. Cela équivaut logiquement à :

```
old = rounding(T)
setrounding(T, mode)
f()
setrounding(T, old)
```

Voir [`RoundingMode`](@ref) pour les modes d'arrondi disponibles.
