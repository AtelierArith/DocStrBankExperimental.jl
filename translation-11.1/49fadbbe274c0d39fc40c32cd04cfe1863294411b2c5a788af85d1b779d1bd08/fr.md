```
Base.Pairs(values, keys) <: AbstractDict{eltype(keys), eltype(values)}
```

Transforme un conteneur indexable en une vue de dictionnaire des mêmes données. Modifier l'espace des clés des données sous-jacentes peut invalider cet objet.
