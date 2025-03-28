```
ffmerge!(repo::GitRepo, ann::GitAnnotated)
```

Fusion de avance rápido de cambios en el HEAD actual. Esto solo es posible si el commit al que se refiere `ann` desciende del HEAD actual (por ejemplo, si se están extrayendo cambios de una rama remota que simplemente está por delante de la punta de la rama local).
