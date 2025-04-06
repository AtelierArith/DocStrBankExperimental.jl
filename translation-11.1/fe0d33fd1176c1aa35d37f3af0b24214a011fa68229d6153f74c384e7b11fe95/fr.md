```
Base.compilecache(module::PkgId)
```

Crée un fichier de cache précompilé pour un module et toutes ses dépendances. Cela peut être utilisé pour réduire les temps de chargement des paquets. Les fichiers de cache sont stockés dans `DEPOT_PATH[1]/compiled`. Voir [Module initialization and precompilation](@ref) pour des notes importantes.
