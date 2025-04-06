```
clear_malloc_data()
```

Efface toutes les données d'allocation de mémoire stockées lors de l'exécution de julia avec `--track-allocation`. Exécutez la ou les commandes que vous souhaitez tester (pour forcer la compilation JIT), puis appelez [`clear_malloc_data`](@ref). Ensuite, exécutez à nouveau votre ou vos commandes, quittez Julia et examinez les fichiers `*.mem` résultants.
