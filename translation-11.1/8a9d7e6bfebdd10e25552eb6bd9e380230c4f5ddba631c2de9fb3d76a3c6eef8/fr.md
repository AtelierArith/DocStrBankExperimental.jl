```
désérialiser(stream)
```

Lire une valeur écrite par [`sérialiser`](@ref). `désérialiser` suppose que les données binaires lues depuis `stream` sont correctes et ont été sérialisées par une implémentation compatible de [`sérialiser`](@ref). `désérialiser` est conçu pour la simplicité et la performance, et ne valide donc pas les données lues. Des données malformées peuvent entraîner l'arrêt du processus. L'appelant doit garantir l'intégrité et la justesse des données lues depuis `stream`.
