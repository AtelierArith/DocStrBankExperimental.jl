```
Threads.atomic_fence()
```

Insérer une barrière de mémoire à cohérence séquentielle

Insère une barrière de mémoire avec des sémantiques d'ordre à cohérence séquentielle. Il existe des algorithmes où cela est nécessaire, c'est-à-dire où un ordre d'acquisition/libération est insuffisant.

C'est probablement une opération très coûteuse. Étant donné que toutes les autres opérations atomiques en Julia ont déjà des sémantiques d'acquisition/libération, des barrières explicites ne devraient pas être nécessaires dans la plupart des cas.

Pour plus de détails, voir l'instruction `fence` de LLVM.
