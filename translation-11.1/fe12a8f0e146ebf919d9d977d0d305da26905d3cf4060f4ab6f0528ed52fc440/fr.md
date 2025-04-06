```
GC.safepoint()
```

Insère un point dans le programme où la collecte des ordures peut s'exécuter. Cela peut être utile dans de rares cas dans des programmes multi-threadés où certains threads allouent de la mémoire (et peuvent donc avoir besoin d'exécuter la collecte des ordures) mais d'autres threads effectuent uniquement des opérations simples (pas d'allocation, de changements de tâche ou d'E/S). Appeler cette fonction périodiquement dans des threads non allouants permet à la collecte des ordures de s'exécuter.

!!! compat "Julia 1.4"
    Cette fonction est disponible depuis Julia 1.4.

